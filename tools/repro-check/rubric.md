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
| Environment Checks | Check the original issue description for the stated environment, then check the claim comment/report for the environment used during reproduction. Look for the operating system, version used, and installation/setup steps.|Pass if the report clearly documents the testing environment and compares it with the original issue, without requiring the environments to match. For a claimed reproduction, the evidence must demonstrate the issue's actual behavior. For a cannot-reproduce report, any relevant environment differences should be documented and considered as a possible explanation for the result. Fail if important environment information is missing, the environment is not meaningfully compared with the issue, or the evidence does not support the claimed result. | required |

|Reproduction of Issue| Check the steps detailed by the person in the claim comment/report that they have followed to reproduce the issue | pass if the claim comment/report's steps are followable and its conclusion (reproduced, or if they claim honestly that they were not able to reproduce the issue) matches what the attached evidence shows. Claims that do more 'telling' of the succeeding of the reproduction without any or much concrete evidence (logs of terminal outputs, artifacts) should not pass the check. If they were able to reproduce the issue, check if the output logs match the expected behaviour shown in the actual issue. | required|

|Proposed Solution|Check for any proposed solution/analysis in the report| The person has detailed or proposed a solution that they think will solve the issue after analyzing it. |preferred|

|Repo's Stated Templates and Contribution Policy|Check repo's issue templates and any AI-assistance disclosure policy against the actual comment text|Pass if the claim and reproduction comments follow the repository's stated contributor communication conventions and communicate a concrete contribution specific to the issue without unrealistic guarantees. If the repository requires AI-use disclosure, the comments must also disclose the AI tool and extent of assistance. Fail if the communication conflicts with stated repository conventions, makes unsupported claims or guarantees, or does not provide a clear, issue-specific contribution intent.|required|


## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes; preferred checks never change the verdict; unclear counts as fail.
