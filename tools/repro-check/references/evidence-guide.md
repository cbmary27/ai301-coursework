# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
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
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

- Where it lives: In an eval bundle, check the issue-context section for the stated target environment (OS, version framework), then the claim comment/repro report's own environment lines for what was actually used. In live mode: the issue thread and the repo's README for supported/required versions.

- What good looks like: the stated target environment (OS, version, framework), then the claim comment/repro report's own environment lines for what was actuallyused. In live mode: the issue thread and the repo's README/CONTRIBUTING for supported/required versions.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

- Where it lives: Check the issue-context section for the detailed steps on how to reproduce the issue, then the claim comment/repro report's steps that the reporter has followed. In live mode: the issue thread.

- What good looks like: The steps start from the initial state all the way upto what triggers the error/issue described. A good list of steps should be able to be followed by a stranger not familiar with the repository; commands are clearly listed along with what inputs to put and what the expected output is.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

- Where it lives: In an eval bundle, check the repro report's observed behavior and the artifacts inlcuded (output excerpts, logs, screenshots, test results, etc). Compare these with the issue-context section to determine what behavior the issue is supposed to produce or what failure it describes. In live mode, check the student's repro report/draft and any linked or included output, logs, screenshots, or test results.

- What good looks like: The artifacts shows the actual result produced by following the reproduction steps and is similar to the result/behavior described in the issue. The artifact should demonstrate the failure rather than just stating that the bug occurred.


## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

- Where it lives: In an eval bundle, check the repro report's section for comments by the reporter. Check whether the report distinguishes between what was observed, what was expected, and what was not tested or could not be reproduced. In live mode, check the student's draft repro comment and the evidence included with it.

- What good looks like: The report should not claim more than what the representing evidence supports. If the reporter could not reproduce the issue, they have honestly written it in the report and also what worked and what didn't. A successful reproduction should identify the observed behavior.


## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

- Where it lives: In an eval bundle, check the claim comment for whether the reporter has analyzed or stated what a potential solution or what they might do as the next step. Also check the issue thread and/or repository documentation/policy for contribution requirements, including any AI-use disclosure requirement. In live mode, check the issue thread, the claim comments, and the repository's README/CONTRIBUTING.md policy. The rules may exist in another file similar to AI_DISCLOSURE.md or a file with a similar name.

- What good looks like: The repro communication describes the observed result and follows the repository's stated contribution or disclosure requirements, including required AI-use disclosure when applicable.

