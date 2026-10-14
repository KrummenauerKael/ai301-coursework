# Rubric: is this pull request ready to submit?

<!--
THIS IS THE PART YOU WRITE (fourth week running; this is the rubric's
final form in the sandbox). Your frame in SKILL.md executes whatever
checks you define here, via your procedure.md. It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the diff read against the plan's scope, the test
     evidence read against the plan's test plan, the description read
     against the diff, the repo-facts block's template asks) or a
     location from your references/evidence-guide.md. "The PR" is not
     a source; "the diff's changed files read against the plan's
     stated boundary" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself
     (does the diff fall inside the plan plus its deviation notes? is
     the claimed evidence observable?), never the write-up's shape
     (how long the description is, how many commits there are).
     Structure-shaped checks are what make graders disagree with
     themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (submit) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. State the `unclear`
   treatment explicitly: the frame here is YOUR SKILL.md, so a rubric
   that stays silent is only covered if your frame's grading
   discipline says what happens (the contract's own default is that
   an unverifiable claim fails).

Cover what actually gets bad PRs submitted. The failure families the
lecture named ARE the harness's scoring categories, same names as the
eval README: silent drift (the diff silently does more or less than
the posted plan, or the description claims fidelity the diff
contradicts), not tested (the evidence proves nothing observable, or
the repo's own checks were never run), unreviewable (debris or
unrelated hunks bury the change), and standards wall (the repo's
stated template and disclosure asks are ignored). Your evidence
guide's four headings map onto these one to one (plan fidelity =
silent drift, test evidence = not tested, diff quality =
unreviewable, standards and comms = standards wall), and the category
floor is scored on exactly these names plus clear accept. A rubric
that ignores a category will fail the eval packages built around
that category. And remember the honest-outcome
rule, fourth week running: a PR that honestly discloses a shortfall
can be ready; a rubric that equates "less than everything" with
"hold" fails the set.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-match | The diff's changed files and hunks, read against the plan's scope, files list, and deviation notes | Pass if every hunk is part of the plan's change or covered by a deviation note, and every planned change is in the diff or deferred in a note. Fail if the diff adds unplanned work (refactors, renames, new options or flags, files the plan doesn't name) or drops a planned change with no note. Removing the issue's xfail marker counts as part of the fix. | required |
| description-honest | The PR title and description, read against the diff | Pass if every claim about what changed is true of the diff. Fail if it claims something the diff doesn't have ("docs updated", "tests added") or says "exactly as planned" / "no other changes" when the diff has unplanned work. | required |
| repro-rerun | The test evidence, read against each item in the plan's test plan | Pass if the evidence re-runs the plan's repro on the branch for every failure the test plan names and states the result after the fix (output, exit code, assertion). Fail if it only says "tested locally" or "works now", only runs a control or a path the fix doesn't touch, or skips a failure the test plan names. | required |
| checks-reported | The test evidence, read against the test suite and checks the repo or the plan names | Pass if the suite and every stated check are named with their outcome. A failing check reported with its reason passes. Pass if nothing is named. Fail if a stated check is never mentioned. | required |
| diff-clean | Every hunk of the diff | Pass if every hunk is the fix, its test, or something the repo asks for. Fail on debug prints, commented-out code, dead functions, new TODOs, or unrelated formatting or import changes. | required |
| template-filled | The repo facts' PR template and stated asks, read against the description and the diff | Pass if every template section has real content and every stated ask is met ("Closes #", checklist, changelog entry). A box left unticked because it isn't true yet, like CI, is fine. Fail if a section is missing or placeholder, an ask is skipped, or a ticked box isn't backed by the evidence. Pass if there's no template and no asks. | required |
| ai-disclosure | The contribution policy line in Repo facts, read against the description | Pass if the policy doesn't require AI disclosure, or it does and the description discloses. Fail if it requires disclosure and there is none. Only "AI use must be disclosed" counts; "comments must be in your own words" doesn't. Live: the course always requires disclosure in Notes for Reviewers. | required |
| commit-messages | The commit list | Pass if every message says what it changes and follows the repo's commit convention. Fail on "wip", "fix", "misc". | preferred |

## Verdict rule

Accept if every required check passes, preferred checks never change the verdict, unclear counts as a fail.
