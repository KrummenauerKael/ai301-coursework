# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
Issue #60: "Faithfulness checker crashes when a context chunk has text: None" — bug in
  rag/evaluator/faithfulness_checker.py, opened by collaborator Andrew Burke, labels: bug, good first issue, rag,
  tier-1.

  ┌─────────────────────────┬───────┬───────────────────────────────────────────────────────────────────────────────┐
  │          Check          │ Grade │                                   Evidence                                    │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ active-repo             │ pass  │ not archived; last push 2026-09-16 (1 day before capture), no releases so     │
  │                         │       │ 90-day push rule applies                                                      │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ maintainer-alive        │ pass  │ 3 commits by Andrew Burke on 2026-09-16 (today)                               │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ unclaimed-issue         │ pass  │ assignees: [], 0 comments, no linked/mentioned PR found for #60               │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ single-deliverable      │ pass  │ single bounded bug: one method (check()), one root cause (.get() default      │
  │                         │       │ doesn't cover None value), with repro steps and a named failing test          │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ settled-direction       │ pass  │ bug report with clear fix location and a named failing test; opener is a      │
  │                         │       │ COLLABORATOR; carries bug/good first issue labels                             │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ ai-policy               │ pass  │ CONTRIBUTING.md (docs/CONTRIBUTING.md) has no AI-contribution restriction —   │
  │                         │       │ only standard workflow/CI/style rules                                         │
  ├─────────────────────────┼───────┼───────────────────────────────────────────────────────────────────────────────┤
  │ beginner-friendly       │ pass  │ carries good first issue label, opened by a collaborator                      │
  │ (preferred)             │       │                                                                               │
  └─────────────────────────┴───────┴───────────────────────────────────────────────────────────────────────────────┘

  All required checks pass → accept. Fit note: this is a Python RAG-evaluation bug (faithfulness checker), matching the
  stated fit profile (Python API, RAG/AI topics).

  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/60",
    "checks": [
      {"name": "active-repo", "grade": "pass", "evidence": "isArchived: false; latestRelease: null; pushedAt
  2026-09-16T21:48:27Z, within 90 days of capture (2026-09-17)"},
      {"name": "maintainer-alive", "grade": "pass", "evidence": "3 commits by Andrew Burke on 2026-09-16, within last 30
  days"},
      {"name": "unclaimed-issue", "grade": "pass", "evidence": "assignees: [], comments: [], no PR mentioning #60 found
  via search"},
      {"name": "single-deliverable", "grade": "pass", "evidence": "Bounded to one bug in FaithfulnessChecker.check()
  with a stated repro and a named failing test test_none_context_chunk_text"},
      {"name": "settled-direction", "grade": "pass", "evidence": "Opened by author_association COLLABORATOR with clear
  root-cause diagnosis; carries bug/good first issue labels, no unresolved thread debate"},
      {"name": "ai-policy", "grade": "pass", "evidence": "docs/CONTRIBUTING.md contains no AI-generation ban or
  restriction, only workflow/CI/style rules"},
      {"name": "beginner-friendly", "grade": "pass", "evidence": "labeled good first issue and tier-1, opened by a
  collaborator"}
    ],
    "verdict": "accept"
  }
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

# eval run written by run_eval.py at 2026-09-17T13:27:42Z
# model: sonnet (pinned)
# graded: ..\..\..\.claude\skills\issue-select
# packages: 20 scored
#   rubric.md  sha256:dad5af01dfe7149e
#   SKILL.md  sha256:bbb295bf984701fd
#
grading 20 bundle(s) with rubric.md, model sonnet, 5 worker(s)...
  issue-04: accept
  issue-03: reject
  issue-02: reject
  issue-06: accept
  issue-05: reject
  issue-01: accept
  issue-07: reject
  issue-08: reject
  issue-09: accept
  issue-11: accept
  issue-12: reject
  issue-10: reject
  issue-14: accept
  issue-13: reject
  issue-16: accept
  issue-15: reject
  issue-17: reject
  issue-18: reject
  issue-20: reject
  issue-19: accept

item      gold    verdict  agree  note
issue-01  accept  accept   yes    
issue-02  reject  reject   yes    
issue-03  reject  reject   yes    
issue-04  accept  accept   yes    
issue-05  reject  reject   yes    
issue-06  accept  accept   yes    
issue-07  reject  reject   yes    
issue-08  reject  reject   yes    
issue-09  accept  accept   yes    
issue-10  reject  reject   yes    
issue-11  accept  accept   yes    
issue-12  reject  reject   yes    
issue-13  reject  reject   yes    
issue-14  accept  accept   yes    
issue-15  reject  reject   yes    
issue-16  accept  accept   yes    
issue-17  reject  reject   yes    
issue-18  reject  reject   yes    
issue-19  accept  accept   yes    
issue-20  reject  reject   yes    

categories: claimed 4/4  clear-accept 8/8  dead-repo 3/3  policy 1/1  scope 4/4
agreement: 20/20 scored items  (bar: 18/20: PASS)

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

Gold Label: {"id": "issue-19", "source": "zxcalc/zxlive#517", "category": "clear-accept", "calibration": false, "verdict": "accept", "note": "maintainer-diagnosed performance bug with named causes, unclaimed"}

issue-19 failed in a previous initial run (did not save the eval-run.md of said run unfortunately)
issue-19  accept  reject   NO     failed: settled-direction

Reason for initial Failure: Failed due to the body of the issue having "potential" and "suggestions" where the run interpreted this lanugage as undecided direction instead of recommended path. The fix was to require the disagreement between two contributors with no maintainer decisions or language that gave direction.



**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

| single-deliverable | the issue title and body | Fails only if the issue is a self-described tracking/umbrella/meta issue, or its work has no stated boundary; spanning the whole codebase or an open-ended set of files. Several similar small items within one component or file is still one deliverable; "several" and "etc." do not by themselves make an issue unbounded. | Required |

This current form passes the evaluation runs while making sure that multi file issues are still accepted, initially had issues with false rejects due to the single file requirment being literal instead of meaning that the issue should not be load bearing of the entire codebase or have a deeper integration with other issues under its umbrella.



**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

There may be an issue where it misses an issue that should be approved due to overlapping files and systems that would otherwise be fairly straightforward and easy to fix. 

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.

   I wanted an issue that was specifically related to RAG or AI/LLM integration, this issue is specifically a Python RAG-evaluation bug.

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
   
   It correctly identified the issue as passing, and specifically took into account my scope request to rank it higher than other 3 issues that were run live as per the assignment. 

3. The anticipated difficulty in claiming it.]

   It appears to be a very straightforward issue about how the text is read  and due to many people's interest in RAG it may be competitive.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
