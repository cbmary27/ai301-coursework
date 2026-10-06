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

Read the plan package in the following order:

1. Repro - Read the reproduction evidence first to establish the concrete bug behavior. Record the observed behavior, the conditions needed to reproduce it, and any specific files, functions, commands, inputs, or outputs identified. Treat this as the baseline for judging whether the diagnosis and proposed changes address the actual reproduced problem.
2. Diagnosis - Read the diagnosis after the repro evidence. Check that the diagnosis explains the behavior established by the reproduction and identifies where the bug occurs. Record the stated cause of the bug, including any referenced files, functions, line numbers, or relevant code paths. Use the repro as the reference point when determining whether the diagnosis is consistent with the observed behavior.
3. Changes -  Read the proposed changes after the diagnosis. Record what the plan proposes to modify, where those modifications will occur, and how they are intended to address the diagnosed cause. Check that the proposed changes are connected to both the diagnosis and the reproduced behavior rather than addressing an unrelated issue.
4. Test - Read the tests last. Record the tests, commands, inputs, expected results, and pass conditions that will demonstrate that the proposed fix works. Check that the tests verify the behavior described in the repro and that their expected results demonstrate that the diagnosed bug has been fixed.

Read the sections in this order because each section provides the reference needed to evaluate the next: Repro -> Diagnosis -> Changes -> Test.

## Evidence gathering

<!-- For each evidence family your rubric's checks name, the concrete
gathering move: which part of the package (or, live, which page or
thread location per your evidence guide) to pull the fact from, and
what to record. A complete procedure leaves no check whose evidence an
executor would have to hunt for. -->

Gather the following evidence from each part of the plan package:

1. Summary -  problem vs. repro evidence. Record the problem described in the Summary. Compare the stated problem with the behavior demonstrated in the Repro section. Note whether the Summary accurately describes the same problem that is reproduced.
2. Repro - file names and expected vs. actual output. Record the file names, functions, commands, inputs, and other locations identified in the reproduction. Record the expected output and the actual output shown by the reproduction. Compare the actual reproduction output with the results described in the Test section to determine whether the test addresses the reproduced behavior.
3. Diagnosis - cause of the bug. Record the stated cause of the error or incorrect behavior.
Record any referenced file names, functions, variables, line numbers, or code paths.
Use these references to determine whether the diagnosis identifies a specific location and cause for the reproduced problem.
4. Changes - locations and proposed modifications. Record the file names and locations where changes are proposed. Record what each proposed change is intended to modify or fix. Compare the proposed file locations with the files and locations identified in the Repro and Diagnosis sections.
5. Test - reproduction steps and expected result. Record the steps, commands, inputs, or conditions needed to run the test. Record the expected output or behavior after the fix. Record the pass condition used to determine whether the test succeeds.Compare the expected test result with the actual behavior shown in the Repro section and verify that the test demonstrates that the reproduced bug is fixed.

## Check execution

<!-- How one check runs against gathered evidence: in what order the
checks execute, what an executor does when evidence for a check is
genuinely absent, and when a check may be graded without re-reading
the whole package. A complete procedure makes two executors grade the
same package the same way. -->

Execute each required check from rubric.md using the evidence gathered in the previous stage.

1. Diagnosis - Compare the plan's diagnosis with the reproduction evidence.
Check whether the diagnosis explains what is causing the reported problem.
Check whether the diagnosis is supported by the observed reproduction evidence.
Pass the check only if both conditions are satisfied.
2. Scope - Examine the files, functions, classes, or other code locations identified in the plan's scope.
Check whether the scope identifies where the bug occurs.
Check whether the plan clearly states what will be changed and what will not be changed.
Pass the check only if the bug location and change boundaries are both clear.
3. Test - Examine the test plan, including its reproduction steps and expected results.
Check whether the steps can be run against the real code and reproduce or validate the reported behavior.
Check whether the expected result demonstrates that the bug is fixed.
Pass the check only if the test is reproducible and its expected result verifies the fix.

If the evidence required for a check is absent, do not infer or invent the missing information. Apply the rubric's rule for missing evidence. The executor may grade a check using the evidence already gathered without rereading the entire package when that evidence is sufficient to make the check's pass/fail decision.

## Verdict assembly

<!-- How the per-check grades become the final accept or reject:
apply your rubric's verdict rule, state how unclear grades enter it,
and say what gets quoted in the output for the deciding check. A
complete procedure produces the same verdict from the same grades,
every time. -->

Apply the rubric's verdict rule to the completed check grades. Since Diagnosis, Scope, and Test are all Required, accept the plan only if all three checks pass. If any required check fails, reject the plan. If a check is unclear or cannot be graded because evidence is missing, apply the rubric's specified rule for unclear or missing evidence. In the final output, state the deciding check and the evidence supporting its grade.
