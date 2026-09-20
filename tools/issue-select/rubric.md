# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Issue is open and unresolved | Issue status shown on the GitHub issue page + Issue body, comment thread, and linked/mentioned pull requests | The issue's current state is labelled as 'OPEN' and there is no maintainer comment or merged pull request indicating that the reported problem has already been fixed or resolved | required |
| Maintainer is alive | Recent default-branch commit dates and maintainer activity in the issue thread | At least 1 maintainer commit or maintainer comment occurred within the last 90 days | required
| Issue is well detailed | Check if the problem that the issue is about has good examples or is well detailed | The issue provides enough concrete information to understand the problem and includes reproduction steps or a concrete example | preferred  |
| Issue is not taken up | Check if someone has already taken up the issue | no assignee, no linked/mentioned PR, no blocking claim. Check the discussion/comment section of the issue to see if anyone has been RECENTLY working on it or has shown any expression of interest (within the last 6 months) regardless of whether there is no assignee. If any of the discussions indicate that the issue has been informally resolved or closed, then block the issue.| required |
| Repository is active | Check the recent commit history of the repository | The recent commits have to be atleast within the last 90 days. | required |
| Issue is ideal for beginners | Issue labels, issue body, referenced files/PRs, and issue discussion | The issue is labeled 'good first issue' OR the issue describes a small, clearly scoped change that does not require major changes or specialized project knowledge | preferred |
| Policy Restriction | There are no policy restrictions that would prevent any kind of contributions to the repository | This policy restriction could be any ranging from prevention of AI usage to requiring maintainer approval to take up the issue | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

ACCEPT if EVERY required check passes; preferred checks NEVER change the verdict, they
rank accepted issues; unclear counts as fail.

