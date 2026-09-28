# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: week 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; your operator swap showed you what that feels
like. Write the map you wish your executor had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

| Signal | In the eval bundle | Live (GitHub / my draft) | What good looks like |
|---|---|---|---|
| Environment record | the "Environment:" line (or block) at the top of `Candidate repro report` | the environment line in my repro draft | One line naming the tool version and the OS the reporter ran, e.g. `yq 4.53.3 (Homebrew), macOS 15.5 (arm64)`. |
| Issue's target version | the version and OS in `Issue`, plus any version `Thread highlights` says the bug occurs on | issue #60's body and comments | A version the issue body gives (e.g. "Version: 4.53.2") or one the thread confirms the bug on (e.g. "confirmed on latest and main"). A version someone pinned as a workaround, where the bug does not occur, is not a target. |
| Version difference | the report's version read against the issue's target  | my draft's version read against issue #60's  | Both versions named somewhere in the report, not necessarily together, e.g. an environment line saying 4.53.3 plus a sentence saying "the issue was filed against 4.53.2; I tested the current release."|




## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

| Signal | In the eval bundle | Live (GitHub / my draft) | What good looks like |
|---|---|---|---|
| Report's commands/input | the command lines and code blocks in `Candidate repro report` | the steps in my repro draft  | The exact commands and input as run, copyable |
| Issue's trigger | the input and command in `Issue` | issue #60's body  | The specific input that causes the bug e.g. `intdict = { 1 = {} }` |
| What the steps depend on | any file, config, or repo the report's steps use | the same in my draft | Every file shown inline or publicly available (a pip package, the public repo). |




## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

| Signal | In the eval bundle | Live (GitHub / my draft) | What good looks like |
|---|---|---|---|
| Report's output | the output, error, or traceback blocks in `Candidate repro report` | the output blocks in my repro draft | The raw output as captured, pasted rather than described, e.g. `panic: not a string` with its trace. |
| Issue's actual behavior | the actual/current result shown in `Issue` | issue #60's body | The failure the issue quotes: its kind (panic, error, wrong output) and its key message |




## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

| Signal | In the eval bundle | Live (GitHub / my draft) | What good looks like |
|---|---|---|---|
| Claims  | "reproduced / confirmed / root cause" sentences in `Candidate claim comment` and `Candidate repro report` | the same sentences in my drafts | Each claim sits next to the output that backs it, e.g. "confirmed on 4.53.2" followed by the 4.53.2 run's output. |
| Cannot-reproduce | a report stating it could not reproduce | the same in my draft | The attempt's output shown plus what differed from the issue, e.g. "uniform name lengths, 2 MiB ARG_MAX." |




## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

| Signal | In the eval bundle | Live (GitHub / my draft) | What good looks like |
|---|---|---|---|
| Claim comment | `Candidate claim comment`, read against `Issue` | my claim draft, read against issue #60 | Names this issue's specifics and a next step |
| AI policy | the "contribution policy" line in `Repo facts` | Path Review's `CONTRIBUTING.md` and any AI policy file | Where disclosure is required, a plain line in the comment, e.g. "I used Claude Code to help draft this." |

