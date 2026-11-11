# Contribution: [Feature]: Track security scans and their progress

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Chris
**GitHub Username:** cbmary27
**Issue:** https://github.com/agntcy/dir/issues/1874
**Pull Request:** [GitHub PR link, once opened]

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: [which tool did this phase's work, and how you used it]
- What it produced: [described in a sentence or a short excerpt]
- Difficulties: [what fought you or fell short, or "none met"]
- What changed: [the patch, revision, or workaround, what you would
  update, or "nothing"]
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 5: Turned my Unit 1 issue-select skill into issue-scout and gave it a search strategy**

I installed the scout over my Unit 1 skill, rewrote my fit profile around good first issues and small bugs in Python, Java, Go and Kotlin, and wrote six `gh search issues` queries plus ranking rules (drop assigned, stale or long-thread issues, one per repo, bugs first, fewest comments). The first scan pulled 558 unique issues and graded the top 5, but "fewest comments first" mostly surfaced issues opened that same day in brand-new repos with 0-28 stars, often filed by the maintainers' own AI agents. My rubric passed them because it has no adoption check, and the ranking let K1rL3s/maxo#388 through with a fixing PR already open, since search results don't carry cross-references (the rubric's "not taken up" check caught it). I logged both gaps in scan-notes.md rather than patching blindly, and took my real picks from the Issue Selection site.

**Unit 6: Installed the voice guard, wrote my Upstream voice rules, and gave Claude a memory file for agntcy/dir**

I added Upstream rules for claims, questions and pings to my voice guide (my vague nomnom comment became a "Wrong" example) and wired the guard in as a Claude Code hook. On Windows that broke twice: `python3` is only a Microsoft Store placeholder, so I changed the hook to call `python`, and Git Bash's `ln -s` silently makes copies, so I used one-line pointer files instead. My claim on #1874 was posted before the guard existed, so I ran the guard's manual check on it afterwards: it stopped my 2026-11-08 comment on my own rule "A claim names my first step and when I'll report back", and repro-check rejected it as not specific to the issue. Only my 2026-11-09 follow-up made the claim pass. While doing that I found that my installed repro-check had been grading with my Unit 3 plan-check rubric, so I restored my Unit 2 rubric from `tools/repro-check/`. I also wrote `CLAUDE.local.md` in my clone (DCO sign-off, the scan subsystem's 4 key files, the exact build and test commands, and the WSL PATH fix Go and Task need), kept out of git with `.git/info/exclude`.

**Unit 7: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 8: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

My scout's own scan of GitHub (558 issues, top 5 graded) mostly turned up brand-new single-author repos, so I took my real candidates from the AI301 Issue Selection site, filtered toward my profile: agntcy/dir#1874 (Go), WorldconVotingSystems/nomnom#277 (Python) and Altinn/altinn-studio#12123 (TypeScript in a C# monorepo). On the first grade, my scout accepted nomnom and Altinn and **rejected #1874** on "Issue is not taken up": another contributor, tnknick14, had volunteered and been assigned in July, inside my 6-month window. Reading the timeline showed that a maintainer unassigned them on 2026-09-03 after asking about progress, and they never opened a PR, so in practice the issue was free. My rubric couldn't tell a released claim from a live one, and it counted my own comments as claims. I patched that check, and after the Unit 6 scope patch the regrade accepted all three: nomnom ranked first on fit (moderate), #1874 second (**ambitious**: whether scan history belongs in a new table or the existing `scan_reports`, and what retention should be), Altinn third.

I chose #1874 over the scout's top-ranked nomnom. It's bigger, but it's more direct: the issue names the table, the states and the API (`NewScan`/`ListScans` keyed on `cid`), so there's less guessing about what the maintainers want. It's in Go, which I'm learning this term, and it's backend API and CLI work, which is the full-stack side I want to get better at. I hope to learn how a real Go service adds a database table, a proto service and a CLI command end to end, and how to work through open design questions with maintainers. Since the difficulty note says ambitious, I raised both open questions in my follow-up before starting. Honestly, the scout's grading held up on the things it checks (it caught an open fixing PR that ranking missed), but it fell short in two ways: its ranking rewards newness, not health, and its claim check only understood claims being made, not released. I fixed the second; the first still needs an adoption check (stars or recent outside contributors) in the rubric.

Claim comment: https://github.com/agntcy/dir/issues/1874#issuecomment-6724098685 (posted 2026-11-08; follow-up with setup and proposed approach: https://github.com/agntcy/dir/issues/1874#issuecomment-6742685664)

**Toolkit**

- Tool: issue-scout. I ran one scan with my search strategy, then graded my three Issue Selection picks directly with my rubric, twice: once as written, then again after the Unit 6 patches.
- What it produced: the scan graded 5 issues (4 accept, 1 reject for an open fixing PR). On my picks, the first grade rejected #1874 on "Issue is not taken up". The regrade accepted it with an "ambitious" difficulty note naming the table-vs-`scan_reports` and retention questions.
- Difficulties: the ranking favored issues opened the same day in tiny new repos, and the rubric has no adoption check. The "not taken up" check treated a claim a maintainer had already released as live, and counted my own comments as claims.
- What changed: I applied the Unit 6 scope patch, replacing my "Issue is ideal for beginners" check with the required "scope-feasible" row plus the difficulty note. I also rewrote "Issue is not taken up" so a maintainer unassigning someone releases their claim and my own comments never block. Still to do: add an adoption check to the rubric.

---

## Understanding the Issue

**Problem Description**

[In your own words, what is broken or missing?]

**Expected Behavior**

[What should happen?]

**Current Behavior**

[What actually happens?]

**Affected Components**

[Which parts of the codebase are involved?]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Reproduction Process

**Environment Setup**

Windows 11 host with WSL2 (Ubuntu 24.04.3 LTS), Go 1.27.2, Task 3.54.0 and Docker Desktop. I cloned https://github.com/agntcy/dir and followed the README's Development section: `task deps`, `task build`, then `task test:unit`, which all passed on `main`. The reproduction ran on a clean worktree of `main` at `226a94c9` (2026-11-11), so my local clone's changes didn't affect it. The issue is a feature request and states no environment; the database tests use in-memory SQLite, so the result doesn't depend on the OS or a running server.

Challenges: Go and Task weren't on the PATH in non-interactive WSL shells, so commands failed with "go: command not found" until I exported `/usr/local/go/bin` and `$HOME/go/bin`. The repo's pre-commit hook (golangci-lint, run through `task`) failed for the same reason, and then reformatted my test file; I re-staged its changes instead of skipping the hook.

**Steps to Reproduce**

Since #2086 (via #2095), `scan_reports` records a completed/partial/failed outcome per record and scanner, so I reproduced the parts of #1874 that are still missing.

1. Check out `main` (I used `226a94c9`) and add `server/database/gorm/scan_history_repro_test.go` from my fork's commit (below). Using the existing test helpers, it writes two scans for the same record and scanner (first `failed` with reason `network`, then `completed`) and expects two `scan_reports` rows.
2. Run `cd server && go test ./database/gorm/ -run TestRepro1874 -v -count=1`.
3. Search for the states and API the issue asks for: `grep -nE "ScanStatus(Completed|Partial|Failed) *=" server/types/database.go`, `git grep -nIE "NewScan|ListScans|security_scans|ScanStatusPending|ScanStatusRunning" -- "*.go" "*.proto"`, and `grep -n "^service" proto/agntcy/dir/security/v1/*.proto`.
4. Observed: the test fails with one row left (the failed scan was overwritten by the completed one). Only completed, partial and failed statuses exist, and both searches for the API return nothing.

**Reproduction Evidence**

- **Commit showing reproduction:** https://github.com/cbmary27/dir/commit/4221fc507877f75addd9858b87cc732cd5665318 (branch `repro/1874-scan-history` on my fork)
- **Screenshots/logs:**

  ```
  scan_history_repro_test.go:29: scan_reports row: status=completed failure_reason="" consecutive_failures=0
  Error:     "[{baeareitestscan... MCP true NONE completed   0 ...}]" should have 2 item(s), but has 1
  Messages:  expected one row per scan (failed, then completed); scan_reports keeps only the latest
  --- FAIL: TestRepro1874_ScanHistoryIsKept (0.02s)
  FAIL	github.com/agntcy/dir/server/database/gorm	0.056s
  ```

  `server/types/database.go` defines only `ScanStatusCompleted = "completed"` (line 221), `ScanStatusPartial = "partial"` (225) and `ScanStatusFailed = "failed"` (228). `git grep` for `NewScan`, `ListScans`, `security_scans`, `ScanStatusPending` and `ScanStatusRunning` exits 1 (no matches), and no `.proto` in `security/v1/` defines a `service`.
- **My findings:** The three gaps #1874 describes are still real on `main`. `ScanReport` is keyed by `(record_cid, scanner_type)` and `UpsertScanReport` (`server/database/gorm/scan.go`) does `ON CONFLICT ... DO UPDATE`, so every scan replaces the last and there's no history. There are no pending or running states. Scans start only from the reconciler's scan task on its interval (`reconciler/tasks/scan/task.go`, via `GetRecordsNeedingScan`); the Go client only has `PushScanReport` and `dirctl` has no scan command, so a user can't request or list scans. Part of the original request (recording outcomes) was already covered by #2086, which I noted in my follow-up comment.

**Toolkit**

- Tool: repro-check, live mode. I graded my claim alone first, then my claim plus repro report together (`claim-draft.md` and `repro-draft.md`), against my Unit 2 rubric and my voice guide.
- What it produced: the claim-only grade rejected my 2026-11-08 comment ("set up the project locally, explore the existing codebase" names nothing specific to the issue). The first full-package grade passed the repro but still rejected on that claim, and flagged that step 2 only showed a snippet of the test. After I added my 2026-11-09 follow-up (part 2 of my claim, as posted) and the fork commit link, it accepted.
- Difficulties: my installed repro-check had been grading with my Unit 3 plan-check rubric and evidence guide ("is this plan ready to post"), probably copied over in Unit 3. My Unit 2 rubric also assumes a bug with an environment to match, which fits awkwardly with a feature request.
- What changed: I restored my Unit 2 rubric and evidence guide from `tools/repro-check/` in my course repo. I pushed the repro test to my fork so the steps link to the full file instead of a snippet. I'd add a line to the rubric's environment check covering issues that state no environment.

---

## Solution Approach

**Analysis**

[Your analysis of the root cause: what is causing the issue, traced
to the files and functions involved.]

**Proposed Solution**

[High-level description of your fix approach, and what you are
deliberately NOT changing.]

**Implementation Plan**

1. [Modify file X to do Y]
2. [Add or change Z]
3. [Update tests]

[Record deviations here as they happen: what changed mid-build and
why. A recorded deviation is honest work; silent drift is not.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Testing Strategy

[What observable checks prove the fix: your reproduction steps re-run
against the built change (before and after), and the repo's own test
suite or checks with the outcome shown. "Tests pass" with nothing
observable named is not a strategy.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Implementation Notes

[A running log, added to as you work. Date each entry. What you
built, decisions you made when you made them, wrong turns included.]

**[Date]**

[Entry]

**[Date]**

[Entry]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Pull Request

**PR Link:** [GitHub PR URL when opened]

**PR Description:** [what the PR says; much of the content above
adapts into it]

**Maintainer Feedback:**

- [Date]: [feedback received, or "none yet"; silence is a normal
  state and costs you nothing]
- [Date]: [how you addressed it]

**Status:** [Awaiting review / Iterating / Merged / Closed. The
status is a fact you record, never a grade: the PR is graded as
opened.]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

---

## Learnings and Reflections

**Technical Skills Gained**

[What you learned technically, named concretely.]

**Challenges Overcome**

[What was hard and how you solved it; point at the real events, the
Toolkit blocks above are full of them.]

**What I'd Do Differently Next Time**

[Reflection on your process.]

---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- [Link to documentation that helped]
- [Discussion, issue, or post that helped]
