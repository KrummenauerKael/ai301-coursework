# Procedure: how this tool grades a PR package

<!--
THIS IS THE PART YOU WRITE (second week running for the procedure).
Week 3 you wrote these steps for a plan package; this week the graded
object is a PR package, and the read that matters most is a
side-by-side: the diff against the plan, the evidence against the test
plan, the description against both. Your week-3 procedure is the
pattern; do not paste it unchanged, because its read order was built
for a different object.

Your rotation is the design brief again, and this week friction routes
three ways: a stall on WHAT to decide is a rubric gap, a stall on
WHERE to look is a procedure gap (this file), and a stall on what the
tool even reads or outputs is a frame gap (your SKILL.md). A complete
procedure lets someone who has never seen a PR package before grade
one exactly the way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
plan's scope pair before opening the diff, and list the files the plan
names" is a step; "understand the change" is a wish.
-->

## Read order

1. Live only: read `scope.md`, then `voice-guide.md`. Stop if the `Repo:` line is a placeholder.
2. Read the plan first. Write down its scope, files, each test plan item, and every deviation note. Reading the plan before the PR keeps the description from framing the diff.
3. Read the repo facts. List the template sections, stated asks, test commands, commit convention, and copy the AI policy line word for word.
4. Read the diff. Write one line per hunk on what it does.
5. Read the commits.
6. Read the test evidence. List each command, before or after, and its result.
7. Read the title and description last. List every claim and every ticked box.

## Evidence gathering

- plan-match: match each hunk to a plan item or deviation note, or "none". Match each plan item to a hunk or a note, or "missing".
- description-honest: match each claim to a hunk, or "not in diff".
- repro-rerun: match each test plan item to an after result on the branch, or "not run". Mark runs that only hit a control path.
- checks-reported: match each stated check to its reported outcome, or "not mentioned".
- diff-clean: mark each hunk fix, test, repo ask, or debris.
- template-filled: match each section and ask to its content, "placeholder", or "missing". Match each ticked box to its evidence.
- ai-disclosure: note if the policy requires disclosure. Quote the disclosure, or "none".
- commit-messages: copy the messages.

## Check execution

1. Run the checks in rubric order, each with only its own evidence.
2. Grade pass, fail, or unclear, and quote the deciding fact.
3. Missing evidence: follow the check's own rule (no template means template-filled passes, no AI policy means ai-disclosure passes, no named checks means checks-reported passes). Anything else missing is unclear.
4. One check never changes another. A good description doesn't pass plan-match.
5. Live: grade only `git diff main...HEAD`. Uncommitted files aren't debris.

## Verdict assembly

1. Apply the verdict rule: accept if every required check passes, preferred never changes it, unclear counts as fail.
2. On reject, name every failing required check. Quote the first one in rubric order as the deciding check.
3. On accept, quote the repro-rerun after result.
4. Put the JSON block last.
