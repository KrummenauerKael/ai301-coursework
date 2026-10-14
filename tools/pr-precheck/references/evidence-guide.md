# Evidence guide: where evidence lives in a PR package

<!--
THIS IS THE PART YOU WRITE (third week running: the map stays in your
hands). Your tool uses this guide as its map: for every kind of
evidence a rubric check names, this file says WHERE to find it in a PR
package and WHAT GOOD LOOKS LIKE when you do.

The four families below are the harness's failure categories under
the names the eval README uses: plan fidelity = silent-drift, test
evidence = not-tested, diff quality = unreviewable, standards and
comms = standards-wall. A package that fails none of them is a
clear-accept. Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the plan-context block's scope pair and test
  plan, the candidate PR's diff, commits, description, or
  test-evidence section, the repo-facts block's template asks and
  stated policy). In live mode (where in your working copy and on
  GitHub: your plan.md and its deviation notes, your branch's diff,
  your draft title and description, your captured test output, the
  repo's PR template and CONTRIBUTING.md).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("every changed file falls inside the
  plan's stated boundary or a deviation note") over adjectives ("the
  diff is clean").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts three ways: your
procedure says WHEN to gather each family, this guide says WHERE, and
your SKILL.md says the tool reads both. Write the map you wish your
executor had.
-->

## Plan fidelity (harness category: silent-drift)

Where it lives: the Plan context (scope, files, deviation notes), read against the Diff, and the Description read against the Diff. Live: my `plan.md` read against `git diff main...HEAD`, and `pr_draft.md` read against that diff.

What good looks like: every hunk is in the plan or a deviation note, every planned change is in the diff or deferred, and every description claim is true of the diff.

## Test evidence (harness category: not-tested)

Where it lives: the Test evidence section, read against the plan's Test plan and the repo's test commands. Live: `test_evidence.md` (repro before on `main`, after on my branch, and the output of `make test-unit`, `make test-integration`, `make lint`, `make typecheck`), read against my plan's Test plan.

What good looks like: the plan's repro re-run on the branch with the after result shown, and the repo's checks named with their outcome. A failing check with its reason counts.

## Diff quality (harness category: unreviewable)

Where it lives: the Diff and Commits. Live: `git diff main...HEAD` and `git log main..HEAD --oneline`.

What good looks like: every hunk is the fix, its test, or a repo ask like removing the xfail marker. No debug prints, commented-out code, dead functions, TODOs, or formatting churn.

## Standards and comms (harness category: standards-wall)

Where it lives: the Repo facts' pull requests and contribution policy lines, read against the Description and Diff. Live: `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`, read against `pr_draft.md`.

What good looks like: every template section filled, "Closes #<number>", only true boxes ticked (CI stays unticked), and AI use disclosed when the policy requires it. Live: the disclosure goes in Notes for Reviewers.