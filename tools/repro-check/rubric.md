# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| trigger-matches | the commands/input in the repro report, read against the input and command in the issue | Pass if the report's input document, expression, and arguments are the same as the issue's, character for character. Changes to how the command is run or delivered (file vs stdin, http vs https, output flags like -v, --offline),file names and paths are allowed. Fail if any character of the input document, expression, or arguments differs, unless the report names the change and why. | required |
| error-matches | the output/error excerpt in the repro report, read against the actual behavior the issue shows | Pass if the report's output shows (1) the same failure kind as the issue (panic/crash, error message, or wrong output) and (2) the issue's quoted error message or wrong value word for word, if the issue quotes one. Ignore paths, memory addresses, and line numbers. Fail if either is missing. If the report states it could not reproduce, this check still passes as cannot reproduce is still acceptable information. | required |
| env-recorded | the "Environment" line in the repro report, read against the version/OS in the issue and any version the thread confirms the bug on | Pass if the report names the software version and OS, and either the version matches the issue's (or one the thread confirms the bug on) or the report states the difference.. If the issue names no version, naming the version and OS is enough. Fail if the version or OS is missing, or if the version differs and the report does not state it. | required |
| steps-reproduceable | the files, configs, or repos the repro steps depend on | Pass if every file, config, and command the steps use is shown in the report, described precisely enough to recreate, or publicly available. Fail if any step depends on something private, unshared, or not specified. | required |
| claim-reproduced | each "reproduced / confirmed / root cause" sentence in the claim comment and repro report, read against the output shown | Pass if every claim of reproduction or cause has matching output shown in the report. A cannot-reproduce passes if it shows the attempt's output and names what differed from the issue. Fail if any claim has no output behind it. | required |
| claim-specific | the claim comment, read against the issue | Pass if the claim comment names something specific to this issue and a concrete next step. Fail if it guarantees a fix, gives a deadline, or could be pasted onto another issue unchanged. | required |
| ai-disclosure | the "contribution policy" line in Repo facts, read against both comments | Pass if the policy has no disclosure requirement, or if it does and a comment discloses AI use. Fail if the policy requires disclosure and neither comment discloses. Only policies that say AI must be disclosed count as requirment. Rules that comments must be human-written or that contributors understand and review their work are not disclosure requirements. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes. Preferred checks never change the verdict. unclear counts as fail.

