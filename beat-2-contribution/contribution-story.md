# Contribution: GET /api/health doesn't report the app version

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Kael Krummenauer
**GitHub Username:** KrummenauerKael
**Issue:** https://github.com/iamvisheshsrivastava/spec2program/issues/32
**Pull Request:** https://github.com/iamvisheshsrivastava/spec2program/pull/33

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Turned issue-select into issue-scout and tested its search strategy on live GitHub**

I turned my unit 1 issue-select skill into issue-scout and wrote a search strategy from my fit profile: three `gh search issues` queries and six ranking rules. Running the queries before the scan showed that the `rag` and `llm` keyword searches each hit the 100-result cap with mostly small personal repos at the top, and a combined `OR` query returned nothing. I added an owner-scoped query on established RAG/LLM projects (llama_index, haystack, ragas and others) and a ranking rule that puts its results first, so the five graded candidates come from maintained projects. My first scan (2026-10-28) rejected all five candidates, all from llama_index, on `unclaimed-issue`: four already had open PRs from their openers that were never linked to the issue, so I added an open-PR search to that check and capped the ranking at two candidates per repo.

**Unit 6: Installed the voice guard project-scoped and folded my voice guide into one copy**

I installed the voice guard inside my course repo (`.claude/voice-guard` and the project `settings.json`) instead of `~/.claude`, because my skills are project-scoped, so the hook points at an absolute path instead of `$HOME`. My three voice-guide copies had drifted (pr-precheck's had one never-post item the others lacked), so I kept the newest as the single guide, symlinked the three skills to it, and added Upstream rules for claims, questions, and pings. A wiring test of the checker stopped `gh issue comment --help` with "no body the guard can read," which is the expected pass. My `CLAUDE.local.md` for ecoscape-connectivity holds the branch and PR rules, how `main.py` reaches `analyze_geotiffs`, and the working Docker commands. I wrote it on 2026-11-01, after the repro and plan, so it hasn't saved me anything yet; it's there for the PR stage.

**Unit 7: Installed the ship-gate next to my project-scoped skills and ran it on my real branch**

I ran the install with its home folder pointed at my course repo, so the ship-gate reads the same project-scoped pr-precheck and voice guide as my other tools, and I added both hooks to my clone's local settings so they fire there. My manifest runs the four CI checks through `docker exec`, because the project needs GDAL 3.13.3, which I only have in the CI image. A full rehearsal before building showed total coverage moving between 85.91% and 86.99%, so I set `fail_under` to 85 instead of 86, and `ruff check` reported `EXE002` on files I didn't change because of the Windows mount, so I moved that rule to the manifest's second table with its reason. On `53-fix-cli-permeability` (2026-10-31) the ship-gate returned PASS: all four checks passed and pr-precheck accepted the branch. That branch never shipped, because the maintainer took #53 back on 2026-11-04. On 2026-11-06 I ran pr-precheck by hand on `32-health-version` for spec2program#32: the first draft failed `ai-disclosure` because the disclosure wasn't under a Notes for reviewers heading, and the revised draft was accepted. Its frame refuses to grade without `plan.md`, `pr_draft.md` and `test_evidence.md` and looks for `docs/CONTRIBUTING.md`, so I graded with the posted plan comment and wrote those three files into the clone afterwards. I opened https://github.com/iamvisheshsrivastava/spec2program/pull/33 on 2026-11-06; GitHub reported it mergeable with no conflicts, and it closes #32.

**Unit 8: Installed the PR monitor project-scoped and ran its state check on both branches**

I installed the PR monitor in `.claude/pr-monitor` beside my other tools. Its first `--state` run, on `53-fix-cli-permeability` (2026-11-04), reported "no-pr-yet", which was right, because #53 never got a PR. On 2026-11-06 I ran `--state` on `32-health-version` a minute after opening PR #33: it read the PR, one passing check, MERGEABLE/UNSTABLE and no review decision, and labelled the state "feedback-in". The only "review" was GitHub Copilot's bot saying it had no quota left, so the monitor counted a bot notice as reviewer feedback. I filled in my playbook the same day. spec2program had no past outside PRs to measure, so I based my 14-day nudge threshold on the owner's commit gaps (9 and 15 days); I allow one nudge, a second only after 30 more quiet days with something new, and I won't close the PR myself. The next `--state` run reported the playbook ready for a full run. I haven't run one yet, because the only "feedback" is the bot notice and there's nothing to answer.

---

## Why I Chose This Issue

My scout's two scans of GitHub (2026-10-28) graded ten RAG/LLM issues and rejected all ten as already claimed, mostly fresh llama_index issues whose openers had PRs ready. My first three picks from the AI301 Issue Selection site went the same way: CTSM #3693 and quality-time #12823 were claimed, and CTSM #126 passed but is a ten-year-old Fortran diff that now touches 25 files in a model that's hard to build outside its own HPC machines. That pushed me to rewrite my fit profile around Python data work instead of AI. The scout, with the unit 6 scope patch, then accepted apache/beam#19246, but I dropped it because reproducing it meant using a BigQuery project, and I wasn't willing to register on another platform for one issue. On 2026-10-31 I searched GitHub directly with `gh search issues` and checked the best results against their threads, PRs and current code. I chose ecoscape-earth/ecoscape-connectivity#53: a maintainer filed it on 2026-10-29 with the good first issue label, a task list and a reproduce command, and it had no assignee, comments or PRs when I checked. It fits my profile because it's a bug in a Python scientific data tool: `main()` passes the permeability CSV to `compute_connectivity` as a raster (`ecoscape_connectivity/main.py:19`). I hope to learn how a small scientific Python project tests its command line, and how its maintainers review a first contribution.

On 2026-11-04 kielni, the maintainer, replied that #53 wasn't written well enough to start work, assigned it to herself and removed the good first issue label. My lecturer told me to find another issue, and I released #53 the same day (https://github.com/ecoscape-earth/ecoscape-connectivity/issues/53#issuecomment-6645252547). With the PR due 2026-11-08, I couldn't wait for another plan approval, so on 2026-11-06 I ran the scout on Python FastAPI and API good first issues and only took ones I could reproduce with a pip install and one request. Four queries returned 277 unique issues. Of the five I graded, aiwaf#34 failed `unclaimed-issue` (open PR #38), and AutomatosAI#1059 passed the rubric but I dropped it, because reproducing it needs Docker with Postgres, Redis and an LLM key, and its CONTRIBUTING.md has contributors wait to be assigned. I chose iamvisheshsrivastava/spec2program#32: the owner filed it on 2026-10-28 with the good first issue label and a task list naming one file and one test, and it had no assignee, comments or PRs. It fits because it's a bug in a FastAPI API that runs on an offline mock LLM, so it needs no key or database. I hope to learn how a small FastAPI project tests its endpoints and how its owner reviews an outside PR.

The scout held up on claims: its open-PR search found PRs that the issue pages never linked, which would have cost me a week on an already-fixed bug. Where it fell short on the wild: my keyword queries returned mostly small personal repos until I added an owner-scoped query, a two-per-repo cap and a rule dropping issues it had already rejected. My unit 1 `single-deliverable` check passed all 13 issues it graded, including CTSM #126, so it never said anything about real size until I replaced it with `scope-feasible` and the difficulty note. The 2026-10-31 search showed the same limit in my `-linked:pr` filter: datasette #2924 still came back open although a merged PR had fixed it, and pandas #58299 came back although main now raises a deliberate error. I'd add a check of the current code for old bugs that might not reproduce anymore.

Claim comment (#53, released): https://github.com/ecoscape-earth/ecoscape-connectivity/issues/53#issuecomment-6545487659, 2026-10-31

Claim comment (#32, claim, repro and plan in one): https://github.com/iamvisheshsrivastava/spec2program/issues/32#issuecomment-6689654937, 2026-11-06

**Toolkit**

- Tool: issue-scout (my search strategy and rubric): two scans of GitHub with my queries, direct grading of three Issue Selection picks before the scope patch and apache/beam#19246 after it, and two direct gradings of ecoscape-connectivity#53 (2026-10-31). On 2026-10-31 I also ran `gh search issues` directly, outside the scout.
- What it produced: both scans rejected all five candidates on `unclaimed-issue`; the first picks gave one accept (CTSM #126, a poor fit) and two claimed rejects; beam#19246 came back accept, difficulty "straightforward on paper", with a may-not-reproduce edge. The direct search produced three unclaimed candidates, led by ecoscape-connectivity#53. The first grading of #53 rejected it on `active-repo`; after my rubric change, the second accepted it, with the difficulty note "ambitious, but only if you take on the optional third task".
- Difficulties: the `rag` and `llm` keyword queries each hit the 100-result cap with personal repos on top, and a combined `OR` query returned 0. The first scan's top 5 were all fresh llama_index issues, already swarmed; `unclaimed-issue` caught them only because a bot comment named the openers' unlinked PRs. The direct search hit GitHub's rate limit partway through, and `-linked:pr` let through issues that were already fixed. `active-repo` rejected #53 even though the repo was pushed the day before, because its latest GitHub release was from 2023 and my rubric only counted a recent push for repos with no releases.
- What changed: changed `active-repo` to pass on a release within 365 days or a push within 90 days, for any repo, after I had already picked #53; added an owner-scoped query and a ranking rule that puts its results first; added an open-PR search to `unclaimed-issue`, a two-per-repo cap, and a rule dropping already-rejected URLs; rewrote my fit profile and queries from AI/RAG to Python data work, with `-linked:pr` and a created-date cutoff; replaced `single-deliverable` with the `scope-feasible` row and added the difficulty note (unit 6 patch). After the 2026-11-06 scan (scan 3 in `scan-output.md`), I logged two gaps in `scan-notes.md` without patching them yet: the rubric has no check on how much setup a repro needs, which let AutomatosAI#1059 pass, and the four FastAPI queries came from that session, not from `search-strategy.md`, whose fit profile still says to avoid LLM projects like spec2program.

---

## Understanding the Issue

**Problem Description**

`GET /api/health` is the app's liveness probe. It reports the active LLM provider and model but not the app version, so there's no way to tell which build a running deployment is. The version also lives in two places: `__version__ = "0.1.0"` in `backend/__init__.py`, and a separate literal `version="0.1.0"` in the `FastAPI(...)` constructor in `backend/main.py`, so the two can drift apart. No test calls `/api/health`.

**Expected Behavior**

The health response includes `"version": backend.__version__`, and the `FastAPI(...)` constructor uses the same constant.

**Current Behavior**

On `d301617` the response has only `status`, `provider`, `model` and `duration_model`: `{"status":"ok","provider":"mock","model":null,"duration_model":{...}}`.

**Affected Components**

`health()` in `backend/main.py` (line 150), the `FastAPI(...)` constructor (line 113), `__version__` in `backend/__init__.py`, and `tests/test_main.py`.

**Toolkit**

- Tool: issue-scout's `scope-feasible` check and difficulty note, then Claude Code reading `backend/main.py` and `tests/` at `d301617` against the issue
- What it produced: one bounded piece of work rated "straightforward", and confirmation that the code still matched the issue: line 113 hardcodes the version and no test references `/api/health`
- Difficulties: none met; the owner's issue already named the file, the constant and the test
- What changed: nothing

---

## Reproduction Process

**Environment Setup**

Windows 11, PowerShell 7.6, Python 3.14.2. I forked iamvisheshsrivastava/spec2program, cloned my fork to `D:\spec2program`, and followed CONTRIBUTING.md: `python -m venv .venv`, `.venv\Scripts\Activate.ps1`, `pip install -r requirements-dev.txt`. `LLM_PROVIDER` defaults to `mock`, so no API key or database setup was needed. Tested on commit `d301617` of `main`.

**Steps to Reproduce**

1. Set up the project as above.
2. Run `uvicorn backend.main:app`.
3. In a second window, run `curl.exe http://127.0.0.1:8000/api/health`.
4. The response has no `version` key.

**Reproduction Evidence**

- **Commit showing reproduction:** `none`. The repro is in my combined comment: https://github.com/iamvisheshsrivastava/spec2program/issues/32#issuecomment-6689654937 (2026-11-06).
- **Screenshots/logs:**

```
> curl.exe http://127.0.0.1:8000/api/health
{"status":"ok","provider":"mock","model":null,"duration_model":{"model_type":"linear","automl":{"candidates_evaluated":["mean_baseline","linear","linear_quadratic_flash"],"cv_mae_by_candidate":{"mean_baseline":1.642,"linear":1.459,"linear_quadratic_flash":1.46},"selection_method":"5-fold cross-validation, lowest mean MAE wins","selected":"linear"},"trained_on_rows":2400,"train_mae_seconds":1.454}}
```

- **My findings:** `health()` at `backend/main.py` lines 158-163 builds the response without the version, line 113 hardcodes `"0.1.0"`, and nothing in `tests/` calls `/api/health`. The issue described this from the code; my run confirmed it on a live server.

**Toolkit**

- Tool: repro-check on the combined claim, repro and plan comment before posting (2026-11-06), with my voice guide
- What it produced: accept, all seven required checks passing. Before that it caught two problems in my pasted draft: copying from rendered chat had turned `backend.__version__` into `backend.version`, and `Python [version]` was still a placeholder.
- Difficulties: my rubric grades a claim and a repro report as two comments, and here they were one. My voice guide's claim-with-a-date-i-can-keep rule wants a report-back date, and I chose not to give one. I also posted the comment with `[version]` still in it, and edited it to `Python 3.14.2` afterwards.
- What changed: I wrapped every code name in backticks so GitHub keeps the underscores. I haven't changed the rubric for combined comments yet.

---

## Solution Approach

**Analysis**

`health()` never reads `backend.__version__`, and `FastAPI(...)` hardcodes the same string separately at line 113, so the version is missing from the response and has two sources.

**Proposed Solution**

Import `__version__` in `backend/main.py`, add it to the health response, and pass it to `FastAPI(version=...)`. I'm not touching the existing `ruff format` differences in `main.py` or the CLI `--version` flag (#31). I posted the plan with the claim and repro (https://github.com/iamvisheshsrivastava/spec2program/issues/32#issuecomment-6689654937, 2026-11-06) and went ahead without waiting for a reply, because the PR is due 2026-11-08 and CONTRIBUTING.md lets good first issues skip straight to a PR.

**Implementation Plan**

1. Add `test_health_reports_app_version` to `tests/test_main.py`, asserting `response.json()["version"] == backend.__version__`, and confirm it fails on `main`.
2. Import `__version__` in `backend/main.py` and add `"version": __version__` to the health response.
3. Replace `version="0.1.0"` with `version=__version__`.
4. Run `pytest` and `ruff check`.

One deviation: I also ran `mypy backend/`, because CONTRIBUTING.md and CI both require it and my posted plan left it out.

**Toolkit**

- Tool: plan-check on the same combined comment (2026-11-06)
- What it produced: accept, all six required checks passing. The preferred `unknowns-stated` check failed: "no test in `tests/` calls `/api/health`" is stated as fact with nothing in the comment backing it, although a grep confirmed it.
- Difficulties: my procedure assumes a separate plan file with in-scope and not-in-scope lines, and here the plan was a section of the posted comment, so plan-check graded the comment as both the plan and the plan comment.
- What changed: I wrote a `plan.md` into the clone afterwards, with scope lines, so pr-precheck had a plan to read. The procedure gap is logged in `scan-notes.md`, not fixed.

---

## Testing Strategy

- **New test, before and after:** `pytest tests/test_main.py -k health -q` failed on `d301617` with `KeyError: 'version'` (`1 failed, 7 deselected`), and passes on `e411398`.
- **Repro re-run:** after the fix, `curl.exe http://127.0.0.1:8000/api/health` returns `{"status":"ok","version":"0.1.0","provider":"mock","model":null,...}`.
- **CI gates** (the three CONTRIBUTING.md names): `pytest` 101 passed, `ruff check .` all checks passed, `mypy backend/` no issues found in 17 source files.
- `ruff format --check` reports 2 files would be reformatted, on lines that predate my change. CI doesn't run it, so I left them alone.

I tested on Python 3.14.2; CI runs 3.11 and 3.12.

**Toolkit**

- Tool: Claude Code running pytest, ruff and mypy in my clone's venv, and pr-precheck grading the branch and PR draft (2026-11-06)
- What it produced: the before/after test results and the three gate results above, saved in `test_evidence.md` in the clone; pr-precheck accepted the second PR draft
- Difficulties: my posted plan named only pytest and ruff check, but CONTRIBUTING.md and `.github/workflows/ci.yml` both require `mypy backend/`
- What changed: I ran `mypy backend/` before opening the PR and added it to the description

---

## Implementation Notes

**2026-11-04**

kielni took #53 back and asked to reorganize the entry points first. I released it the same day. My local commit `53ceba8` on `53-fix-cli-permeability` was never pushed.

**2026-11-06**

Scanned for FastAPI good first issues and chose spec2program#32. Forked, cloned and reproduced it: venv, `pip install -r requirements-dev.txt`, uvicorn, curl. Posted one comment with claim, repro and plan (16:19 UTC). Wrote the failing test, made the three-line fix, and ran the CI gates; all passed. Committed as `e411398` ("Report app version in /api/health (#32)") on `32-health-version`, pushed to my fork, and opened PR #33 at 16:30 UTC, 11 minutes after the comment. Wrong turn: I posted the comment with `Python [version]` still in it and fixed it with an edit.

**Toolkit**

- Tool: Claude Code, editing `tests/test_main.py` and `backend/main.py` in my clone and running the tests; I ran the git commands myself
- What it produced: the test and the fix (11 insertions, 2 deletions across two files)
- Difficulties: an earlier attempt to install the repo's dependencies in Claude Code's own scratch folder was blocked by its sandbox, so the first reproduction ran in my own terminal
- What changed: nothing

---

## Pull Request

**PR Link:** https://github.com/iamvisheshsrivastava/spec2program/pull/33

**PR Description:** "Report app version in /api/health (#32)". It says what changed and why, lists the two files, closes #32, gives before/after curl output and the three CI gate results, and under Notes for reviewers mentions the untouched `ruff format` lines, that I tested on Python 3.14.2 while CI covers 3.11 and 3.12, and that I used AI-assisted tooling and reviewed and tested every change myself. The repo has no PR template; the description follows CONTRIBUTING.md's pull request process.

**Maintainer Feedback:**

- 2026-11-06: none yet (PR opened the same day).

**Status:** Awaiting review (2026-11-06).

**Toolkit**

- Tool: pr-precheck on the branch and PR draft before opening, then the PR monitor's `--state` check on PR #33 (2026-11-06)
- What it produced: pr-precheck rejected the first draft on `ai-disclosure` and accepted the second; the monitor reported PR #33 as mergeable with one passing check and labelled it "feedback-in"
- Difficulties: pr-precheck's frame expects `plan.md`, `pr_draft.md` and `test_evidence.md`, which I hadn't written for #32 yet. The monitor's "feedback-in" came from a Copilot bot notice about quota, not from a person.
- What changed: I moved the AI disclosure under a Notes for reviewers heading and wrote the three files into the clone. I'd change the monitor to skip bot reviews when it picks the state; not done yet.

---

## Learnings and Reflections

**Technical Skills Gained**

- Testing a FastAPI endpoint in-process with `TestClient`, and writing the test first so it fails with the exact error (`KeyError: 'version'`) before the fix.
- Keeping one source of truth for a version string: importing `__version__` from the package instead of repeating the literal in `FastAPI(...)`.
- Running a project's real CI gates locally (pytest, ruff, mypy) by checking CONTRIBUTING.md against `.github/workflows/ci.yml`, instead of only the checks I had put in my plan.
- From #53: running a project in its CI Docker image when my own machine can't match a pinned dependency (GDAL 3.13.3).
- Working from a fork: `origin` for my branch, `upstream` for the original repo, and a PR from fork to `main`.

**Challenges Overcome**

- Claimed issues. My first two scans rejected all ten graded candidates as already claimed, mostly through open PRs that the issue pages never linked. I added an open-PR search to my rubric, which then caught aiwaf#34's open PR #38 on 2026-11-06.
- Losing #53. I had a passing branch, but the maintainer took the issue back on 2026-11-04. I released it in the thread the same day and re-scanned with a tighter constraint: a repro that needs only a pip install and one request.
- Heavy setups. Beam#19246 needed a BigQuery project and #53 needed a pinned GDAL in Docker. For #32 I filtered for a mock-LLM app with no key or database, and opened the PR 11 minutes after posting my claim (comment 16:19 UTC, PR 16:30 UTC).
- Markdown eating my code. Copying my draft from rendered chat turned `backend.__version__` into `backend.version`; wrapping every code name in backticks fixed it.

**What I'd Do Differently Next Time**

- Start with how heavy the reproduction is. Two of my three chosen issues were blocked by setup or by the maintainer before any code mattered, and #32, the one with the lightest setup, went from claim to PR in one day.
- Post one comment with claim, repro and plan when the issue is a well-specified good first issue. Waiting for plan approval on #53 cost a week and ended with the maintainer rescoping it.
- Check the comment in GitHub's Preview before posting. I posted `Python [version]` and had to edit it.
- Fill in the playbook before opening the PR, so it's ready before the monitor's first run instead of after it.

---

## Resources Used

- spec2program's CONTRIBUTING.md (https://github.com/iamvisheshsrivastava/spec2program/blob/main/CONTRIBUTING.md): the venv and `pip install -r requirements-dev.txt` setup, the note that the mock LLM needs no key, the three CI gates, and the pull request process I followed.
- The issue's own task list (https://github.com/iamvisheshsrivastava/spec2program/issues/32): it named the file, the constant and the test, and my plan follows its three tasks.
- spec2program's `.github/workflows/ci.yml`: confirmed the gates CONTRIBUTING.md lists, including `mypy backend/`, plus a `duration_model` check, all of which I ran before opening the PR.
- ecoscape-connectivity's `.github/workflows/tests.yml` (for #53): pointed me to the `ghcr.io/osgeo/gdal:ubuntu-small-3.13.3` image I reproduced in.
- kielni's reply on ecoscape-connectivity#53 (2026-11-04): explained why the issue wasn't ready to work on, which is why I moved to #32.
