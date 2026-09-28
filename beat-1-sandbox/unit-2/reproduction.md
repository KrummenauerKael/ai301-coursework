# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

KrummenauerKael

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60#issuecomment-5863255407

Hi, I would like to have a try at this issue. I'll reproduce the `TypeError` when a context chunk has `text: None` in the FaithfulnessChecker on Windows. I'll report with the details after I reproduce this error.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60#issuecomment-5863652260

**Reproduction of issue #60**

Environment: commit `f89c06f` (main), Python 3.14.2, Windows 11, set up with `make setup` per docs/SETUP.md.

Steps:
From the repo root in Git Bash:

```
.venv/Scripts/python -c "from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])"
```

Output:
```
Traceback (most recent call last):
  File "<string>", line 1, in <module>
    from rag.evaluator.faithfulness_checker import FaithfulnessChecker; FaithfulnessChecker().check('Knows Python.', [{'text': None}])
                                                                        ~~~~~~~~~~~~~~~~~~~~~~~~~~~^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "D:\ai301-coursework-fork\pathreview-ai301-fa26-s1\rag\evaluator\faithfulness_checker.py", line 38, in check
    context_text = " ".join([chunk.get("text", "") for chunk in context_chunks])
TypeError: sequence item 0: expected str instance, NoneType found
```

Expected: check() treats a chunk with text: None like a missing text and returns a faithfulness score (0.0-1.0) instead of crashing.

Actual: check() raises TypeError: sequence item 0: expected str instance, NoneType found at faithfulness_checker.py line 38, where " ".join(...) receives the None returned by chunk.get("text", "").

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

agreement: 2/3 scored items
agreement: 2/2 scored items
agreement: 2/3 scored items
agreement: 3/3 scored items
agreement: 20/20 scored items
agreement: 18/20 scored items
agreement: 1/2 scored items
agreement: 2/2 scored items
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 19/20 scored items
agreement: 1/1 scored items
agreement: 20/20 scored items

**Package analysis**

pkg-03  accept  reject   NO     failed: ai-disclosure

Rubric rejected it when gold label accepted. The issue was that the rubric failed it by seeing the "human-written requirement" as a form of AI disclosure necessity when in reality AI usage was allowed, the comments were the only requirement to being human-written, rubric didn't differentiate.

**Check rationale**

| ai-disclosure | the "contribution policy" line in Repo facts, read against both comments | Pass if the policy has no disclosure requirement, or if it does and a comment discloses AI use. Fail if the policy requires disclosure and neither comment discloses. Only policies that say AI must be disclosed count as requirment. Rules that comments must be human-written or that contributors understand and review their work are not disclosure requirements. | required |

'Rules that comments must be human-written or that contributors understand and review their work are not disclosure requirements.' This section had to be added due to the check failing and considering a requirement for comments to be written as humans as a no AI policy.

**Trade-offs**

pkg-11 had to be rerun because it would sometimes fail due to filename and path changes it was then changed to pass better by allowing 'innocent' changes to running parameters.
pkg-05 also would fail occasionaly due to steps-reproduceable. fixing small details about it and specifics of what were truly necessary for a pass solved the borderline fails/pass 
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
