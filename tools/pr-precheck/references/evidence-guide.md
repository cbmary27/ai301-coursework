# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

**Where it lives:** In eval mode, inspect the plan-context block’s scope, test plan, and deviation notes, then compare them with the candidate PR’s diff, commits, and description. In live mode, inspect `plan.md`, its `## Deviations` section, the branch diff, and `pr_draft.md`.

**What good looks like:** Every changed file and behavior falls within the plan’s stated scope, or an omission or deviation is explicitly documented. The PR description accurately describes what the diff delivers; unreported extra changes or missing planned work are silent drift.

## Test evidence (harness category: not-tested)

**Where it lives:** In eval mode, inspect the test-evidence section and compare it with the plan-context test plan and reproduction steps. In live mode, inspect `test_evidence.md`, captured before/after results, and outputs from the repository’s test, lint, and type-check commands.

**What good looks like:** Evidence identifies the behavior tested, expected result, command or reproduction steps, and observable outcome. Claims such as “tests pass” without supporting output, or missing results for planned checks, are insufficient.

## Diff quality (harness category: unreviewable)

**Where it lives:** Inspect the candidate PR’s unified diff and commit list in eval mode. In live mode, inspect the current branch’s diff and commits.

**What good looks like:** The change directly addresses the issue and is understandable in review. Unrelated edits, debug leftovers, dead code, commented-out blocks, unnecessary formatting churn, or unrelated commits make the change harder to review.

## Standards and comms (harness category: standards-wall)

**Where it lives:** In eval mode, inspect the repo-facts block’s PR template, contribution instructions, stated policies, and maintainer directions. In live mode, inspect the repository’s PR template, `CONTRIBUTING.md`, relevant issue or maintainer instructions, and the draft PR title and description.

**What good looks like:** Required PR sections contain specific, truthful information; issue references, testing details, and required AI-use disclosure are present. Explicit maintainer instructions are addressed rather than ignored or answered with boilerplate.