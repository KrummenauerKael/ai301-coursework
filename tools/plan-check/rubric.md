# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| scope-bounded | The plan's in-scope and not-in-scope statements and its files list, read against the problem the Issue reports | The change fixes the one reported problem and every named change is needed for that fix. Fail if it adds refactors, features, fixes for other bugs, or "let me fix this while I'm here" work. Moving related work into not-in-scope or a follow-up passes. | required |
| maintainer-aligned | Thread highlights: comments from the repo's maintainers (OWNER, MEMBER or COLLABORATOR), read against the plan's approach and the plan comment | The plan follows the direction those comments set, or the plan comment names that direction and explains why it differs. Fails if the plan contradicts or ignores it. Passes if there are no such comments. | required |
| cause-grounded | The plan's diagnosis, read against every step of the repro evidence, especially control runs and debug output | Pass if the stated cause explains every behavior the repro shows, including what the control runs rule out. Fail if any repro step contradicts the cause, if the plan calls repro evidence a "red herring" without testing it, or if it adopts a diagnosis from the thread that the repro rules out. | required |
| ai-disclosure | The "contribution policy" line in Repo facts, read against the plan comment | Pass if the policy has no disclosure requirement, or if it has one and the plan comment discloses AI use. Fail if the policy requires disclosure and the comment does not disclose. Only policies that say AI use must be disclosed count as a requirement. Rules that comments must be human-written or human-voiced, or that contributors must understand their changes, are not disclosure requirements. | required |
| unknowns-stated | The plan's risks or unknowns section and the plan comment's certainty language, read against what the repro actually showed | Pass if every claim the repro does not prove is stated as an unknown or a deferral. Fail if the plan or comment states as certain something the repro never showed. | preferred |
| test-correctness | The plan's test plan, read against the repro evidence's steps | Pass if the test plan names a specific command or test and the observable result that proves the fix (an exit code, output, assertion or value), tied to the reproduced failure. Fail if it only says "ran fine", "run the full test suite", "feels like its better", "should all be fixed" or names no observable outcome for the fix itself  | required |
| executable | The plan's files list and approach steps | Pass if the plan says where the change goes (files or a specific code path) and commits to one change a stranger could start on without asking anything. Pinning exact functions during the build is fine. Fail if the location is vague, more than one approach is left open, or the main work is still finding the problem instead of fixing it. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes, preferred checks never change the verdict, unclear counts as a fail. 