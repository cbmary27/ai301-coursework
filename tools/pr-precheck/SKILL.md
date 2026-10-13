---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Determine whether exactly one PR package is ready to submit. A package includes the plan and deviations, issue, diff, PR title and description, and test evidence. Judge these artifacts against the issue, plan, rubric, and repository requirements.

## Inputs and modes

- **Live mode:** Read `plan.md` and its deviations, the issue thread, the branch diff from `git diff main...HEAD`, `test_evidence.md`, `pr_draft.md`, the repository PR template, and `docs/CONTRIBUTING.md`. For a house-chain submission, use the supplied house plan and repro pack instead.
- **Eval mode:** Grade one complete package from the supplied bundle. Use only its contents; fetch nothing and read no external files. Run every check and apply the complete verdict rule.

## The scope seam (live mode only)

Read `scope.md` before anything else. If `Repo:` contains a placeholder, stop and ask the student to fill it with their section's Path Review repository. Refuse to grade work outside the specified repository. Ignore `scope.md` in eval mode.

## The voice seam (live mode only)

Read `voice-guide.md` and check the PR title and description against its rules. Report violations in the summary. Voice violations alone do not change the verdict unless a rubric check explicitly uses them. Ignore the voice guide in eval mode.

## Component reads

Read `rubric.md` for checks and the verdict rule, `procedure.md` for the grading steps, and `references/evidence-guide.md` to locate evidence. Follow the procedure as written; report gaps rather than inventing steps. If `rubric.md` or `procedure.md` has no actual content, refuse to grade.

## Verdict and output

Return `accept` when the rubric's acceptance conditions are met; otherwise return `reject`. End the response with the following valid fenced JSON block, with nothing after it.

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

- **Evidence first:** Cite the fact or quote supporting every grade.
- **Grade the change, not its polish:** Compare the diff, plan, issue, test evidence, and repository requirements.
- **The rubric decides:** Never change a check's meaning during a run.
- **The procedure decides how:** Report missing steps instead of improvising.
- **Unclear defaults to fail:** Follow the rubric's rule; if it is silent, treat unverifiable claims as failing.