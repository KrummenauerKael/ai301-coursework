# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

KrummenauerKael

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60#issuecomment-6029522403

Hi, here's my plan for this one, built on the repro I posted above.

The crash comes from line 38 of faithfulness_checker.py: chunk.get("text", "") only falls back to "" when the key is missing, so {"text": None} passes None into " ".join(...). I plan to change that line to chunk.get("text") or "" and remove the xfail marker on test_none_context_chunk_text, as CONTRIBUTING.md asks.

Not in scope: the word-overlap matching in _is_supported(), which is a separate issue.

To check the fix, I'll re-run my repro command (expecting a score between 0.0 and 1.0 instead of the TypeError) and run test_none_context_chunk_text plus make test-unit. I'll build it on fix/60-faithfulness-none-text in my fork.

## Your branch

**Branch**

fix/60-faithfulness-none-text

**Evidence**

Environment: fork `KrummenauerKael/pathreview-ai301-fa26-s1`, branch `fix/60-faithfulness-none-text` (base commit `f89c06f`), Python 3.14.2, Windows 11, Git Bash from the repo root, the same setup as my Unit 2 repro.

**Before** (branch created, no code changed yet), my Unit 2 reproduction command:

```
$ .venv/Scripts/python -c "from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])"
Traceback (most recent call last):
  File "<string>", line 1, in <module>
    from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])
                                                                        ~~~~~~~~~~~~~~~~~~~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "D:\ai301-coursework-fork\pathreview-ai301-fa26-s1\rag\evaluator\faithfulness_checker.py", line 38, in check
    context_text = " ".join([chunk.get("text", "") for chunk in context_chunks])
TypeError: sequence item 0: expected str instance, NoneType found
```

**After** (line 38 changed to `chunk.get("text") or ""`, issue #60 xfail marker removed), the same command:

```
$ .venv/Scripts/python -c "from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])"
2026-10-06 22:33:02 [info     ] faithfulness_checked           claims_count=1 score=0.0 supported_count=0
```

The same call with `print(...)`, per my test plan:

```
$ .venv/Scripts/python -c "from rag.evaluator.faithfulness_checker import FaithfulnessChecker; print(FaithfulnessChecker().check('Knows Python.', [{'text': None}]))"
2026-10-06 22:33:29 [info     ] faithfulness_checked           claims_count=1 score=0.0 supported_count=0
0.0
```

The checker's test file, with `test_none_context_chunk_text` now passing without its marker (the 3 xfails are issue #59 tests):

```
$ .venv/Scripts/python -m pytest tests/unit/test_faithfulness_checker.py -q
..x...x......x........                                                   [100%]
19 passed, 3 xfailed in 1.31s
```

The full unit suite:

```
$ make test-unit
...
tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_none_context_chunk_text PASSED
tests/unit/test_faithfulness_checker.py::TestFaithfulnessChecker::test_missing_text_key_in_chunk PASSED
...
376 passed, 52 xfailed, 1 warning in 9.21s
```

No traceback, and a score of `0.0` (inside 0.0–1.0) where the before run crashed at line 38.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. agreement: 4/5 scored items  - pkg-14 failed: executable, pkg-02 did not run due to UTF error
2. agreement: 1/2 scored items  - --only pkg-02 and pkg-14, pkg-14 failed: executable
3. agreement: 1/1 scored items  - pkg-14 pass fix implemented as mentioned below
4. agreement: 20/20 scored items - all pass
5. agreement: 19/20 scored items - pkg-14 failed: cause-grounded, unknowns-stated, executable removed a typo
6. agreement: 6/7 scored items -  --only pkg-14,pkg-09,pkg-01,pkg-11,pkg-16,pkg-17,pkg-18, pkg-14 failed: unknowns-stated, executable changed the cause-grounded and executable lines in procedure.md
7. agreement: 1/1 scored items - --only pkg-14
8. agreement: 19/20 scored items - pkg-14 failed: unknowns-stated, executable

**Package analysis**

pkg-14. Gold label: accept. My rubric rejected it on `executable` in runs 1 and 2, accepted it in runs 3 and 4, and rejected it again in runs 5, 6 and 8. Run 8 is the final run in `eval-run.txt`.

It failed because my executable check said "Pass if the plan names the files it will change". pkg-14 doesn't list files, just code paths.

What made it pass is that I changed the check to "Pass if the plan says where the change goes (files or a specific code path)". Runs 6 to 8 used the same wording, and pkg-14 still passed in run 7 but failed in runs 6 and 8, so it sits on the edge of "Fail if the location is vague". Gold calls it "arguable on the deferral".

**Check rationale**

| executable | The plan's files list and approach steps | Pass if the plan says where the change goes (files or a specific code path) and commits to one change a stranger could start on without asking anything. Pinning exact functions during the build is fine. Fail if the location is vague, more than one approach is left open, or the main work is still finding the problem instead of fixing it. | required |

It used to say "Pass if the plan names the files it will change". However, as seen above, a plan with no file names but with sufficient information of what it would change was mistakenly rejected. By accepting a specific code path instead of only file names, pkg-14 passed in runs 3, 4 and 7.

**Trade-offs**

Loosening `executable` to accept "a specific code path" instead of named files risked passing the unbuildable packages: pkg-10, pkg-17 and pkg-18 don't name files either. Run 8, the full run in `eval-run.txt`, confirms it didn't: all three are still `reject` and agree with gold (`unbuildable 3/3`). The cost is pkg-14, which still fails `executable` in some runs; I accepted 19/20 instead of loosening the check further.


---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
