# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

1. Read the repro evidence first. Write down every step, what it shows, and what each control run rules out.
2. Read the issue and the thread highlights. Write down the one reported problem in one sentence, and quote any comment from an OWNER, MEMBER or COLLABORATOR that sets a direction.
3. Read the repo facts. Copy the contribution policy line word for word.
4. Read the candidate plan. Write down its diagnosis, in-scope and not-in-scope lines, files, approach, and test plan.
5. Read the plan comment last, the way a maintainer on the thread would.


## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

- scope-bounded: list every change the plan names. Mark each one "needed for the reported problem" or "extra". Deferred or not-in-scope work is not a named change.
- maintainer-aligned: use the maintainer quotes from read order step 2. For each one, note if the plan or comment follows it, explains why it differs, or ignores it.
- cause-grounded: take the plan's diagnosis. Mark each repro step "consistent", "contradicts", or "not addressed". Any "contradicts" fails. "Not addressed" is fine unless that step is a control run whose result the diagnosis can't produce; mark that one "contradicts".
- ai-disclosure: use the policy line from read order step 3. Note if it requires AI disclosure, and if the plan comment discloses.
- unknowns-stated: list the certainty words in the plan and comment ("root cause is", "definitely", "will fix"). For each one, note if a repro step backs it.
- test-correctness: quote the test plan's command or test and its expected result. Note which repro step it re-runs.
- executable: write down the files list. Flag hedge words: "somewhere", "maybe", "whichever", "not sure", "investigate", "profile", or a choice between two approaches left undecided. Two words for the same action are not two approaches.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

1. Run the checks in rubric order. Each check uses only its own gathered evidence.
2. Grade every check pass, fail, or unclear, and quote the fact that decided it.
3. If the evidence is missing, follow the check's own rule: no maintainer comments means maintainer-aligned passes, and no AI policy means ai-disclosure passes. Any other missing evidence is unclear.
4. One check's grade never changes another's. A well-written plan does not pass cause-grounded because it reads well.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

1. Apply the rubric's verdict rule: accept if every required check passes. Preferred checks never change the verdict. Unclear counts as fail.
2. On reject, name every failing required check and quote its deciding evidence.
3. On accept, quote the test plan's expected result.
4. Put the JSON block last.