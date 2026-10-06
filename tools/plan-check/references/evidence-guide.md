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

Where it lives:
Look at the candidate plan's Diagnosis section and the Repro evidence. Use the reproduction evidence as the reference for the behavior the diagnosis must explain.

What good looks like:
The diagnosis identifies what is causing the reported problem and is supported by the behavior shown in the reproduction evidence. The stated cause should not contradict or ignore the reproduced behavior.

## Scope

<!-- Where the plan bounds itself: the in-scope statement, the
not-in-scope line, the files or areas named. What one bounded change
looks like next to a drive-by rewrite. -->

Where it lives:
Look at the candidate plan's Scope/Changes section, including the files, functions, classes, or other code locations identified for modification.

What good looks like:
The scope identifies where the bug occurs and clearly defines what will and will not be changed. The identified locations should be specific enough to distinguish the intended fix from unrelated code changes.

## Executability

<!-- Where the plan says what will actually be done: files or areas,
approach, order of work. What it means for a stranger to be able to
start executing without asking the author anything. -->

Where it lives:
Look at the candidate plan's Changes section for the proposed implementation approach and the locations where work will be performed.

What good looks like:
The plan identifies concrete files or code areas and describes the changes to be made clearly enough for the implementation to be understood.

## Test plan

<!-- Where the plan says how success will be observed, and how that
maps onto the repro evidence's steps and artifacts. What a decisive
test plan names that a vague one does not. -->

Where it lives:
Look at the candidate plan's Test section, including its test steps, reproduction steps, commands or inputs, and expected results. Compare these with the Unit 2 reproduction evidence.

What good looks like:
The test plan provides reproducible steps that can be run against the real code and states an expected result that demonstrates the bug is fixed. The test should verify the behavior established by the reproduction evidence.

## Honesty

<!-- Where claims meet uncertainty: risks, unknowns, and deviations.
How to tell stated unknowns from false confidence, and where an
honest mid-build deviation gets recorded. -->

Where it lives:
Look for stated risks, assumptions, unknowns, limitations, or deviations in the candidate plan.

What good looks like:
Any uncertainty or limitation that affects the proposed fix is explicitly identified rather than presented as a certainty. If no relevant uncertainty is stated, do not infer one.

## Comms

<!-- Where the words meet the thread and the repo: the plan comment
read against the issue's maintainer signals (thread highlights, or
the live thread) and against the repo-facts block's stated templates,
contributing asks, and contribution policy (including AI-use
disclosure requirements). What thread-aware looks like next to
boilerplate. -->

Where it lives:
Look at the plan comment and, where provided, the issue/thread context and repo-facts block.

What good looks like:
The plan's communication is consistent with the issue context and any stated repository or contribution requirements. Relevant maintainer guidance or required disclosure is addressed rather than ignored.
