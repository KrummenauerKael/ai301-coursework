---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

<!--
THIS IS THE PART YOU WRITE, and it is the last one: the frame itself.
Weeks 1 through 3 handed you a working SKILL.md and you filled the
files behind it; this week the frame ships as headings, and you write
what it says. The frontmatter above and the section headings below are
fixed (CONTRACT.md's layout rule); the instructions under each heading
are yours. Write instructions to the tool, in the imperative, the way
weeks 1-3's frames spoke to you: what to read, in what order, what to
refuse, what to emit. Your executor in the rotation is the test: a
frame gap they hit (cannot tell what the tool reads, or how a verdict
gets assembled) is a missing sentence here.

One section is not yours: the JSON schema in "Verdict and output" is
reproduced from CONTRACT.md verbatim and may not be altered. Your
words decide everything around it.
-->

## The question

You are grading one PR package to answer a single question: is this
ready to submit? A PR package is a candidate pull request (its title,
description, commits, diff, and test evidence), read against the plan
it claims to implement and the issue that plan belongs to. You do not
answer any other question, you never grade more than one package per
run, and you do not answer from gut feel: you execute `procedure.md`,
which applies `rubric.md` to evidence gathered per
`references/evidence-guide.md`.

## Inputs and modes


**Live mode**: my own PR before I open it. Run from my fork clone, on my branch. Read:

- `scope.md` and `voice-guide.md` in this skill folder
- `plan.md`, including `## Deviations`
- the diff: `git diff main...HEAD`, and the commits: `git log main..HEAD --oneline`. Only committed changes count.
- `pr_draft.md`: line 1 is the title, the rest is the description
- `test_evidence.md`
- the issue thread: `gh issue view <number> --repo <scope repo> --comments`
- `.github/PULL_REQUEST_TEMPLATE.md` and `docs/CONTRIBUTING.md`

A house-chain student reads the house plan and repro pack instead. `plan.md`, `comment.md`, `pr_draft.md` and `test_evidence.md` are never committed; that's not a finding.

**Eval mode**: the bundle is the whole world. Use only the bundle text. Don't fetch or run anything. Grade every check with the full verdict rule.

**Refuse to grade** when:
- `rubric.md` or `procedure.md` is empty
- live: the `Repo:` line is a placeholder, or the issue isn't in the scoped repo
- live: `git diff main...HEAD` is empty, or `plan.md` is missing
- more than one package is given

If `pr_draft.md` or `test_evidence.md` is missing, grade the checks that need it unclear and say which file is missing.

## The scope seam (live mode only)

Read `scope.md` first. If the `Repo:` line is still a placeholder, stop and tell me to fill it with my section's Path Review repo. Never guess. Refuse any issue outside that repo. Follow its house rules. Eval mode ignores `scope.md`.

## The voice seam (live mode only)

Read `voice-guide.md` next. Check the PR title and description against each rule. In the summary, list any rule the draft breaks, with the sentence that breaks it. It never changes the verdict. Eval mode ignores `voice-guide.md`.

## Component reads

`rubric.md` has the checks and the verdict rule. `references/evidence-guide.md` says where each kind of evidence lives. Follow `procedure.md` exactly. If it's missing a step, say so in the summary; don't make one up. If `rubric.md` or `procedure.md` has no content, stop and say the tool can't grade without them.

## Verdict and output

`accept` means submit, `reject` means hold. Nothing else. Print one line per check (name, grade, deciding fact), then voice notes in live mode. In live mode, use the issue URL as `item`. End with this JSON block, with nothing after it:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
```

## Grading discipline

- Every grade names the fact or quote that decided it.
- Grade the diff against the plan, not how good the description sounds.
- If a check passes by its rule, it passes, even if it feels wrong.
- Follow the procedure as written and report its gaps.
- Unclear counts as fail.
- A shortfall the plan and description both state honestly can still be ready.