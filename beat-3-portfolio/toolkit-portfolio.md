# Toolkit Portfolio

Path: `beat-3-portfolio/toolkit-portfolio.md`

**Student:** Chris Mary Benson

## Featured Tools

I chose issue-scout, repro-check and plan-check because they are the tools I have the most evidence to talk about. Each one was calibrated against an eval set in the sandbox units and then used live on my real issue, agntcy/dir#1874, where it made a call I could check: issue-scout first rejected #1874 and then accepted it after I fixed its claim check, repro-check rejected my first claim comment and accepted my follow up, and plan-check rejected my first plan for missing a test plan and accepted it once I added one.

**1. issue-scout**

**What it is, and the judgment hole I wrote:** 

- What it does: grades a GitHub issue as a first contribution (accept/reject, with evidence per check), or searches all of GitHub, ranks results cheaply, and grades the top few
- Started as issue-select in Unit 1 (the PathReview sandbox); became issue-scout in Unit 5 (any public repo)
- My judgment, `rubric.md`: 7 checks, Issue is open and unresolved, Maintainer is alive, Issue is well detailed (preferred), Issue is not taken up, Repository is active, scope-feasible, Policy Restriction
- My judgment, `search-strategy.md` (Unit 5): fit profile (good first issues and small bugs, Python/Java/Go/Kotlin), six `gh search issues` queries, ranking filters (drop assigned/stale/long threads, one per repo, bugs first, fewest comments)
- My log, `scan-notes.md`: what each scan got wrong, dated
- Course given: `SKILL.md` frame and `scope.md`

**How it evolved, dated:** 

| Date | What happened |
|---|---|
| 2026-09-19 | Unit 1 submitted (commit `2171831`, "Files to be submitted"). Eval agreement went 8/20, then 16/20, then 19/20 (bar 18/20, PASS). |
| Unit 1 calibration | "Issue is not taken up" was revised because "an old expression of interest was incorrectly treated as evidence that an issue was currently taken up". It was changed to look at recent activity (within 6 months). |
| 2026-11-04 | First real scan: 6 queries, 558 unique results, 5 graded. |
| 2026-11-10 | Graded my 3 Issue Selection picks directly. #1874 was rejected on "not taken up". |
| 2026-11-10 | Unit 6 scope patch: "Issue is ideal for beginners" (preferred) became the "scope-feasible" row (required), plus a Difficulty note. |
| 2026-11-10 | Patched "not taken up": a maintainer unassigning someone releases their claim, and my own comments never count. |
| After the patch | The regrade accepted #1874 with an "ambitious" difficulty note. |

**Evidence:**

- Unit 1 run history (from `selection.md`):
  `agreement: 8/20 ... category floor unmet: no match in claimed, policy` -> `16/20 ... no match in policy` -> `19/20 scored items (bar: 18/20: PASS)`
- scan notes, 2026-11-04: "Ranking 'fewest comments first' mostly surfaced issues opened that same day, so 0 comments meant 'new', not 'free'."
- scan-notes, 2026-11-04: "Ranking let K1rL3s/maxo#388 through with an open fixing PR (#396), because search results don't carry cross-references; the rubric's 'Issue is not taken up' check caught it."
- scan-notes, 2026-11-10: "#1874 was rejected on 'Issue is not taken up': tnknick14 volunteered and was assigned on 2026-07-23, even though maintainer lgecse unassigned them on 2026-09-03 and they never opened a PR."
- **Before/after pair:** #1874 graded reject on "not taken up" (before the patch), then accept with an "ambitious" difficulty note (after it), both on 2026-11-10.

**2. Repro-check**

**What it is, and the judgment hole I wrote:** 

- What it does: grades a claim comment and reproduction report against their issue and answers "ready to post?" (accept/reject); claim-only mode early, full package before the repro goes out
- My judgment, `rubric.md`: 4 checks, Environment Checks, Reproduction of Issue, Proposed Solution (preferred), Repo's Stated Templates and Contribution Policy (includes the AI-disclosure rule from pkg-20)
- My judgment, `references/evidence-guide.md`: where each check's proof lives in a package and on GitHub
- Live mode also holds drafts against my voice guide (now a pointer to the voice guard's copy)
- Course given: `SKILL.md` frame and `scope.md`

**How it evolved, dated:**

| Date | What happened |
|---|---|
| 2026-09-27 | Unit 2 submitted (commit `f6d846d`). Eval agreement went 18/20, then 19/20, then 17/20, then 19/20 (PASS). |
| Unit 2 calibration | pkg-10: the rubric said reject, gold said accept. A cannot-reproduce report on a different environment, with the differences documented. I revised "Environment Checks" so a mismatch doesn't auto-fail a cannot-reproduce report. |
| Unit 2 calibration | Then pkg-11 failed: gold reject, a *claimed* reproduction on a materially different environment. Refined again: a claimed reproduction needs a comparable environment. |
| Unit 2 calibration | pkg-20: made the disclosure check stricter, so a missing AI-use disclosure fails when the repo requires one. |
| 2026-11-08 / 11-09 (Unit 6) | Live on #1874: the claim-only grade rejected my 2026-11-08 comment. The full package (claim plus repro) passed the repro but still rejected the claim. After my 2026-11-09 follow-up and the fork commit link (`4221fc50`) were added, it accepted. |
| Unit 6 | Found the installed repro-check was grading with my Unit 3 plan-check rubric and evidence guide ("is this plan ready to post"). Restored my Unit 2 rubric from `tools/repro-check/`. |

**Evidence:** 

- Unit 2 run history (from `reproduction.md`): `18/20 ... no match in disclosure` → `19/20 ... no match in disclosure` → `17/20` → `19/20 scored items (bar: 18/20: PASS)`
- The 17/20 dip came after I changed the rubric for pkg-10, which then broke pkg-11. I described this in "Package analysis".
- Story, Reproduction Toolkit: the claim-only grade rejected my 2026-11-08 comment because "set up the project locally, explore the existing codebase" names nothing specific to the issue.
- My real claim comments, for a before/after pair:
  - 2026-11-08: "Hi! I'd be interested in picking up this issue. I'll set up the project locally, explore the existing codebase, and follow up on this thread with my proposed approach." (https://github.com/agntcy/dir/issues/1874#issuecomment-6724098685)
  - 2026-11-09, the follow-up that made it pass: setup and versions, what #2086/#2095 already cover, what's still missing, a proposed approach, and two numbered questions. (…#issuecomment-6742685664)
- Result afterwards: both maintainers answered the two questions within two days (2026-11-11, …6795743395 and …6797562597).

**3. Plan-check**

**What it is, and the judgment hole I wrote:**

- What it does: grades a plan (`plan.md`) and a draft plan comment against the issue and my reproduction, and answers "ready to build from?" (accept/reject); in the wild the comment is never posted
- My judgment, `rubric.md`: 3 required checks, Diagnosis (cause explains the reproduced behavior), Scope (where the change goes, what won't change), Test (runnable steps plus an expected result that shows the fix)
- My judgment, `procedure.md`: the grading steps themselves (read order Repro → Diagnosis → Changes → Test, evidence gathering, check execution, verdict assembly); new in Unit 3, when the workflow moved out of `SKILL.md` and into my hands
- My judgment, the evidence guide
- Course given: `SKILL.md` frame and `scope.md`

**How it evolved, dated:**

| Date | What happened |
|---|---|
| 2026-10-06 | Unit 3 submitted (commit `0801572`). Eval agreement 19/20 (PASS) in one run. |
| Unit 3 | pkg-20 miss: the rubric said accept, gold said reject. "my rubric does not have requirements to check for disclosure statements in the plan and to compare them with the repo's required contribution policy and disclosure usage." |
| 2026-11-12 (Unit 7) | First live run on my #1874 plan (`plan.md` and `plan-comment.md`): **reject**. Diagnosis pass, Scope pass, Test **fail**. |
| 2026-11-12 | Added a 7 step Test plan (commands plus expected results) to Solution Approach and the expected result to the comment. |
| 2026-11-12 | Second run: **accept**, all three checks passing. |

**Evidence:**

- First run, Test: `"grade": "fail", "evidence": "plan.md has no runnable test steps or expected result (tests appear only as files to add in steps 5, 7, 10); plan-comment.md says 'rerun my reproduction on the branch' without stating the result that shows the fix"`
- Second run, Test: `"grade": "pass", "evidence": "plan.md Test plan step 2: 'cd server && go test ./database/gorm/ -run TestRepro1874 -v -count=1 ... Expected: it passes, with two security_scans rows (failed with reason network, then succeeded) and still one scan_reports row', against step 1's expected failure on main"`
- Verdicts: `"verdict": "reject"`, then `"verdict": "accept"`.
- My Unit 3 check rationale for Scope: "I also included what will and will not be changed so that the scope of the proposed solution is clearly defined and does not expand beyond the issue."

## Inventory

- pr-precheck (Unit 4): Checks a PR before submission by reviewing the plan, tests, code changes, and PR description. It initially failed due to stale main and Windows Git issues, but passed all four rubric checks after the fixes on Nov 16.

- Voice guard (Unit 6): A Claude Code hook that checks GitHub comments and PR messages against my personal communication guidelines. It’s working on Windows and has already blocked a couple of messages that didn't meet my standards.

- Ship-gate and manifest (Unit 7): Runs the required unit tests, lint checks, and PR precheck before allowing a PR to be created. It passed on Nov 16 at 4:37 PM, before the file-mode fix.

- CLAUDE.local.md (Unit 6): A local memory file for my agntcy/dir project that keeps important project details, commands, DCO requirements, and my WSL PATH fix. It's excluded from Git, so it stays local.

## The Arc

**Beat 1**

Date: September 2026 (Unit 1)
Friction: The evaluation scored only 8/20 because old expressions of interest were being mistaken for active claims, causing mismatches in the claimed and policy categories.
Change: Updated the rules so that "Issue is not taken up" only considers recent activity and fixed the policy checks.
Result: The score improved to 16/20, then 19/20 (PASS), and I selected issue #53 on PathReview.

**Beat 2**

Date: September 2026 (Unit 2)
Friction: pkg-10 was rejected despite having a well-documented cannot-reproduce report, while fixing it caused pkg-11 to fail with 17/20.
Change: Split the environment check so documented cannot-reproduce reports could pass with an environment mismatch, while claimed reproductions still required comparable environments.
Result: The evaluation improved to 19/20 (PASS).

**Beat 3**

Date: October 2026 (Unit 3)
Friction: plan-check accepted pkg-20 even though the gold evaluation rejected it. I also noticed there were no disclosure or policy checks.
Change: No fix was implemented; I documented the missing checks as a gap.
Result: none

**Beat 4**

Date: November 4, 2026 (Unit 5)
Friction: My initial repository scan surfaced same-day issues in repositories with 0–28 stars, including one that already had an open fixing PR.
Change: Documented these problems in scan-notes and started using the Issue Selection site to find actual candidates.
Result: I selected issue #1874 directly from the site rather than relying on the scan.

**Beat 5**

Date: November 10, 2026 (Unit 5/6)
Friction: The scout rejected #1874 because it still treated a claim as active even after the maintainer had released it.
Change: Updated the rules so unassigning releases a claim, my own comments don't count, and added a scope-feasibility check.
Result: The regrade accepted #1874, with an "ambitious" note.

**Beat 6**

Date: November 10, 2026 (Unit 6)
Friction: repro-check was grading claims using checks intended for plans, which meant the wrong rubric had been installed.
Change: Restored the original Unit 2 rubric from tools/repro-check/.
Result: The grading was corrected, and repro-check rejected my November 8 claim.

**Beat 7**

Date: November 8–9, 2026 (Unit 6)
Friction: My voice guard and repro-check both rejected my original claim because it was too generic.
Change: Posted a more specific follow-up describing my proposed approach and asking two numbered questions.
Result: repro-check accepted the follow-up, and two maintainers responded within two days and agreed with the design.

**Beat 8**

Date: November 10, 2026 (Unit 6)
Friction: The voice-guard hook wasn't working properly on Windows because python3 pointed to the Microsoft Store stub and ln -s behaved differently than expected.
Change: Switched the hook to use python and replaced the symlinks with pointer files.
Result: The hook's wiring test successfully stopped the outgoing command as expected.

**Beat 9**

Date: November 12, 2026 (Unit 7)
Friction: plan-check rejected my #1874 plan because the Test section in plan.md didn't include actual commands or expected results.
Change: Added a seven-step test plan to Solution Approach and recopied it into plan.md.
Result: The second plan-check run accepted the plan.

**Beat 10**

Date: November 12–16, 2026 (Unit 7)
Friction: The ship-gate couldn't access my WSL clone because of Git's dubious ownership warning, the hook used the wrong Python command, and the checks needed to run inside WSL.
Change: Added safe.directory, switched the hook to python, and configured the manifest to run commands through wsl -e bash -lc.
Result: Both checks passed when run through the gate, and the hook test produced two expected stops. On November 16 the gate first stopped because my own pr-precheck rejected the branch, which turned out to be a stale local `main` and Windows git phantom changes; after I fixed those, the gate passed at 4:37 PM with all four pr-precheck checks passing.

## Limitations and What's Next

- Bug shaped rubrics: repro-check's environment check and plan-check's "where the bug occurs" assume a bug; #1874 was a feature request and fit loosely
- Nothing checks the tools themselves: a wrong rubric sat installed in repro-check unnoticed until its checks talked about "plans"
- Setup-sensitive on Windows + WSL: `python3` stub, `ln -s` copies, Windows git "dubious ownership", stale local `main` and CRLF/file-mode phantoms each made a tool stop on a branch that was fine
- No disclosure/contribution-policy check in plan-check (pkg-20 miss, Unit 3), still unfixed
- What's next:
  - issue-scout: add an adoption check (stars, contributors, age) and check linked PRs before ranking
  - repro-check: an environment line for issues that state no environment; a version line in each rubric so a mismatch is visible
  - plan-check: a procedure step for a reproduction quoted in the drafts but not posted; a disclosure check
  - toolkit: a setup check (python, git `safe.directory`, base branch up to date) before any tool runs

**Tool limits.**

issue-scout: no adoption check, so brand-new tiny repos still pass "maintainer alive" and "repo active"; search results don't show linked PRs, so the ranking can't see an issue that's already being fixed
repro-check: its environment check assumes a bug with a stated environment, which fits a feature request poorly, and nothing in it confirms which rubric is installed
plan-check: no step for a reproduction that's only quoted in the drafts, not posted, and no check for disclosure or contribution policy
