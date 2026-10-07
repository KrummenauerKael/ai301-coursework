# Evidence guide: where evidence lives in a plan package

<!--
THIS IS THE PART YOU WRITE (second week running: the judgment files
stay in your hands). The skill uses this guide as its map: for every
kind of evidence a rubric check names, this file says WHERE to find it
in a plan package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repro-evidence block,
  the candidate plan's scope statement or test plan, the plan comment,
  the repo-facts block). In live mode (where on GitHub or in the
  draft: the issue thread, the student's posted repro comment, the
  repo's docs, the draft plan and comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the stated cause cites behavior the
  repro evidence actually shows") over adjectives ("diagnosis is
  solid").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute, and this week that cuts twice: your
procedure.md tells the skill WHEN to gather each family, and this
guide tells it WHERE. Write the map you wish your executor had.
-->

## Diagnosis and grounding

<!-- Where the plan states its cause, and where the repro evidence
pins down the behavior that cause must explain. What it means for a
diagnosis to follow from the evidence rather than contradict or
ignore it. -->

Where it lives: the plan's Diagnosis section, read against every step of the Repro evidence block, especially control runs and --debug or traceback output. Live: my draft plan.md, read against my posted repro comment on the issue.

What good looks like: the stated cause explains every step the repro shows, including why the control runs behave differently.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

Where it lives: the plan's in-scope and not-in-scope lines and its Files list, read against the problem in the Issue section. Live: my draft plan.md, read against the issue body.

What good looks like: every named change is needed to fix the one reported problem. Related work moved into not-in-scope or a follow-up is fine.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

Where it lives: the plan's Files and Approach sections. Live: my draft plan.md.

What good looks like: a stranger knows which file to open and which change to make there, without asking anything.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

Where it lives: the plan's Test plan section, mapped onto the Repro evidence steps. Live: my draft plan.md, mapped onto my posted repro comment's command and output.

What good looks like: it names a specific command or test and the observable result that proves the fix (exit code, output, assertion, or value), and re-runs the reproduced failure. 


## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

Where it lives: the plan's risks, unknowns, or deferral lines, and the certainty words in the plan and comment ("root cause is", "definitely"). Live: also the Deviations section of my plan.md after the build.

What good looks like: anything the repro doesn't prove is stated as an unknown or deferred.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

Where it lives: the plan comment, read against the Thread highlights (comments marked OWNER, MEMBER, or COLLABORATOR) and the Repo facts contribution policy line. Live: the issue thread on codepath/pathreview-ai301-fa26-s1 and the repo's docs/CONTRIBUTING.md.

What good looks like: the comment follows or engages any maintainer direction in the thread, and discloses AI use if the policy says AI use must be disclosed. A policy that only says comments must be human-written does not require disclosure.