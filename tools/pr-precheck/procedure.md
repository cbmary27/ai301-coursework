# Procedure: how this tool grades a PR package

## Read order

1. Determine whether the run is live or eval.
2. In live mode, read `scope.md` first and refuse if the repo is outside scope or the `Repo:` line is a placeholder. In eval mode, use only the package bundle.
3. Refuse if `rubric.md` or `procedure.md` has no actual content.
4. Read the issue, then `plan.md` and its deviations, before inspecting the diff.
5. Read test evidence, the PR title and description, and the repository's PR template and contribution policy. In live mode, also read `voice-guide.md`.

## Evidence gathering

1. Record the issue's requirements and the plan's intended changes and tests.
2. Compare the complete diff against the plan. Identify missing planned changes, undocumented changes, and unrelated edits.
3. Compare test evidence against the plan's test steps and required repository checks. Record actual outputs, including failures.
4. Compare every PR description claim against the diff and test evidence. Check required template sections, issue references, and AI-use disclosure.
5. Use `references/evidence-guide.md` to locate evidence. Record a specific fact or quotation for every check.

## Check execution

1. Run every check in `rubric.md` in its listed order, following its pass condition and weight.
2. Grade each check `pass`, `fail`, or `unclear` based on evidence. Do not invent missing evidence or assume unverified claims are true.
3. If evidence is missing, check the specified locations before grading. Apply the rubric's rule for unclear results; if unspecified, treat unclear as failing.
4. Report live-mode voice-guide violations separately unless the rubric explicitly makes them affect the verdict.

## Verdict assembly

1. Apply the verdict rule in `rubric.md` to all check grades. Return only `accept` or `reject`.
2. If multiple checks fail, identify the first failing required check in rubric order as the main reason for rejection.
3. Provide a concise per-check summary with evidence.
4. End with the contract's exact fenced JSON schema, listing every check in rubric order. Use the PR URL in live mode or package ID in eval mode. Ensure the JSON is valid and nothing follows the final block.