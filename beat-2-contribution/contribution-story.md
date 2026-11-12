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

Directory security-scans the records (agent descriptions) it stores, but it only remembers the latest result. Each scan of a record overwrites the previous one, so there's no history of past scans, no way to see that a scan is waiting or in progress, and no way for an admin to ask for a scan or list a record's scans. Part of the original request was already covered by #2086 (fixed in #2095), which added a completed/partial/failed outcome to `scan_reports`. What's still missing is history, pending/running states, and an API and CLI to start and list scans.

**Expected Behavior**

Every scan attempt should be kept as its own row, so a record's rows make up its scan history, with progress states (`pending` → `running` → `succeeded`/`failed`). An admin should be able to request a scan by record CID (`NewScan`) and list a record's scans, optionally by status (`ListScans`). The design was agreed with the maintainers on the issue thread: akijakya proposed a separate history table and answered my two questions ([comment](https://github.com/agntcy/dir/issues/1874#issuecomment-6795743395)), ramizpolic agreed and asked for no cleanup job yet and admin-only auth ([comment](https://github.com/agntcy/dir/issues/1874#issuecomment-6797562597)), and I confirmed what I'd build ([my reply](https://github.com/agntcy/dir/issues/1874#issuecomment-6807933518)).

**Current Behavior**

`scan_reports` keeps exactly one row per record and scanner, and every scan replaces it. In my reproduction, a failed scan followed by a completed scan leaves one row: the failure is gone. The only statuses are completed, partial and failed. Scans only start when the reconciler's background task picks a record on its interval, and there is no RPC, Go client call or `dirctl` command to start or list them.

**Affected Components**

- `server/database/gorm/scan.go`: the `ScanReport` model and `UpsertScanReport`, which overwrites the row
- `server/types/database.go`: the scan status constants and the database interfaces
- `server/database/gorm/record.go` and `migration.go`: the `Record` model's cascading relations and the list of tables `AutoMigrate` creates
- `reconciler/tasks/scan/task.go`: the only place scans run (`Run`, `scanRecord`, `recordOutcome`)
- `utils/scanner/`: the MCP, Skill and A2A runners (`merge()` in `mcp.go` drops the scanner version)
- Later, for PR 2: `proto/agntcy/dir/security/v1/`, `server/controller/`, `server/authz/`, `client/scan.go`, `cli/cmd/`

**Toolkit**

- Tool: Claude Code with `gh` and `git grep`, reading the issue thread and only the scan subsystem's code, then distilling it into my `CLAUDE.local.md`.
- What it produced: a map of where scans live (`scan.go`, `types/database.go`, the reconciler's scan task, the runners) and confirmation that nothing named `NewScan`, `ListScans`, `security_scans`, pending or running exists.
- Difficulties: the issue was opened before #2086/#2095, which already covered part of it, so I had to separate what was still missing from what was done.
- What changed: I scoped the issue to the remaining gaps (history, progress states, API/CLI) and said so in my follow-up comment.

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

The missing history comes from how `scan_reports` is keyed. `ScanReport` (`server/database/gorm/scan.go`) has a primary key of `(record_cid, scanner_type)`, and `UpsertScanReport` does `ON CONFLICT ... DO UPDATE`, so each scan replaces the last. That table is also read by scheduling (`GetRecordsNeedingScan`), search filters, policy facts and pruning as "the current state", so it can't hold history without changing all of those readers. There are no pending/running states because the only statuses (`server/types/database.go`) describe a scan's result, not its progress. And there's no API because scans are only started by the reconciler's scan task (`reconciler/tasks/scan/task.go`): `Run` picks records through `GetRecordsNeedingScan`, `scanRecord` runs the MCP, Skill and A2A runners, and `recordOutcome` writes the result.

**Proposed Solution**

Following the design agreed with the maintainers ([akijakya](https://github.com/agntcy/dir/issues/1874#issuecomment-6795743395), [ramizpolic](https://github.com/agntcy/dir/issues/1874#issuecomment-6797562597)):

- A new `security_scans` table with one row per scanner run, grouped by a `scan_id` for one pass over a record. It has progress statuses (`pending`, `running`, `succeeded`, `failed`), a trigger (`scheduled` or `manual`), `scanner_version`, `requested_by`, timestamps, and a copy of the verdict.
- When a scanner finishes, its `security_scans` row and the `scan_reports` upsert are written in the same transaction, so history and current state never disagree.
- A foreign key to `records` with `ON DELETE CASCADE`, like `scan_reports`.
- A manual scan starts as one placeholder row with an empty `scanner_type`, because only the reconciler finds out which scanners apply to a record. The first scanner that runs takes it over.

The work is split into two PRs. **PR 1 (this story):** the table and the reconciler recording history. **PR 2:** the `NewScan`/`ListScans` Admin API with auth rules, the Go client and `dirctl`.

Deliberately not changing: what `scan_reports` means or how it's written (same rows, same retry schedule), scheduling, search filters, policy facts, ingest of peers' reports, and the scanner interface. No retention or cleanup job (ramizpolic asked for that to be a separate issue). Selecting a single scanner in `NewScan` is left out; the issue only asks for a CID.

**Implementation Plan**

PR 1, layer 1 (storage):

1. `server/types/database.go`: progress statuses, triggers, the `SecurityScanObject` interface, and a `SecurityScanDatabaseAPI` interface added to `DatabaseAPI`.
2. New `server/database/gorm/security_scan.go`: the `SecurityScan` model with indexes, and the methods `CreatePendingScan` (dedup and cooldown), `ListPendingScans`, `StartScannerRun`, `FinishScannerRun`, `DiscardScannerRun`, `CloseScanPlaceholder`, `FailStuckScans` and `ListScans`.
3. `server/database/gorm/scan.go`: move `UpsertScanReport`'s logic, unchanged, into a helper that runs inside the caller's transaction.
4. `record.go`: add `SecurityScans` with `OnDelete:CASCADE`. `migration.go`: add `SecurityScan{}` to `AutoMigrate`. A new table needs no numbered migration.
5. Tests in `security_scan_test.go`, plus no-op stubs in `reconciler/tasks/signature/task_test.go`, whose fake implements the whole database interface by hand.

PR 1, layer 2 (reconciler), planned:

6. `reconciler/tasks/scan/task.go`: fail stuck scans at the start of each run, run pending manual scans, give each pass a `scan_id`, wrap each scanner run in `StartScannerRun` → `FinishScannerRun` (or `DiscardScannerRun` if it didn't apply), and close unused placeholders.
7. `utils/scanner/mcp.go`: carry the scanner version through `merge()`.
8. Reconciler tests with a fake DB and fake runners, checking that `scan_reports` gets exactly the same writes as before.

Deviations so far:

- **Two PRs instead of one** (2026-11-11), so the schema gets reviewed before the API is built on it.
- **Column `scan_trigger` instead of `trigger`**, because `TRIGGER` is an SQL keyword and this package writes raw `Where` strings.
- **No "claim" step for pending scans** (2026-11-11). My first version flipped a request to `running` as soon as the reconciler picked it up, before any scanner ran. I changed it so a request stays `pending` until its first scanner starts, which keeps `running` meaning one thing everywhere. That's safe because the reconciler runs as a single replica (`replicas: 1`) and never overlaps its own runs.
- **Added `DiscardScannerRun`** (2026-11-11). Scanners only find out they don't apply to a record after they've run, so the row created when they start has to be removed, or handed back as the placeholder, when they don't apply.

**Toolkit**

- Tool: the issue thread with the maintainers, plus Claude Code reading the reconciler and scanner code; my own handoff notes kept the decisions in one place between sessions.
- What it produced: the agreed design, a two-PR split, and the layer 1 file list above.
- Difficulties: the thread left open what a pending row is, and the scanner interface only has `Name()` and `Run()`, so a scanner can't say it doesn't apply until it has run.
- What changed: the placeholder-takeover design, `DiscardScannerRun`, and keeping requests `pending` until a scanner starts. These are recorded as deviations above and will go in the PR description. I haven't run plan-check on this plan yet.

---

## Testing Strategy

**Reproduction, before and after.** Before: my repro (two scans of the same record and scanner, failed then completed) leaves one `scan_reports` row and no history anywhere. After: the same two scans leave **two** `security_scans` rows (`failed` with reason `network`, then `succeeded`) **and still one** `scan_reports` row with the latest result. My repro test asserted two `scan_reports` rows, which the agreed design deliberately doesn't do, so it stays on my fork as the reproduction only. Its "after" is `TestFinishScannerRun_KeepsHistoryWhileScanReportsOverwrites`.

**Storage (layer 1), done.** 13 unit tests in `server/database/gorm/security_scan_test.go`, on in-memory SQLite like the repo's existing scan tests. They cover history kept while `scan_reports` still overwrites, the verdict and scanner version copied, a failed write rolling back the `scan_reports` upsert, dedup and cooldown in `CreatePendingScan`, `ListPendingScans` changing nothing, placeholder takeover, discarding a scanner that didn't apply (deleted, or handed back as the placeholder), closing an unused placeholder, only old `running` rows failed as interrupted, list order/filter/paging, and cascade on record delete. Command: `cd server && go test ./database/gorm/ -count=1`.

**Nothing existing changed.** The 26 existing scan, upsert, scheduling and cascade tests must still pass, and `git diff -w server/database/gorm/scan.go` should show only the function split, no logic change.

**Reconciler (layer 2), planned.** Tests with a fake DB and fake runners for a scheduled pass, a manual scan, a scanner that doesn't apply, a scanner failure, and a record that can't be pulled, each checking that `scan_reports` gets exactly the writes it gets today.

**The repo's own checks.** `task test:unit` and the repo's golangci-lint (run through its pre-commit hook) must pass. These will be the rows of my ship-gate manifest.

**End to end, planned.** One real run with the reconciler and at least one scanner installed: scan a record twice and show two history rows plus one `scan_reports` row. This goes in my PR description as the observable proof.

**Toolkit**

- Tool: `go test` on in-memory SQLite, the repo's golangci-lint through its pre-commit hook, and `task test:unit`.
- What it produced: 13 passing layer-1 tests, 0 lint issues in `server` and `reconciler`, and a full `task test:unit` pass (107 packages ok) on the first layer-1 version.
- Difficulties: the first lint run found 4 issues in my code (3 unwrapped errors and a 17-method interface); unit tests can't exercise the real scanners; and I changed layer 1 after that full-suite run, so it needs re-running.
- What changed: I wrapped the errors and exempted the interface with `//nolint:interfacebloat`, following the repo's own precedent in `server/types/signature.go`. I added an end-to-end run to the plan for real evidence.

---

## Implementation Notes

**2026-11-08**

Claimed #1874 with a short comment. My voice guard and repro-check later both flagged it as too generic.

**2026-11-09**

Set the project up in WSL2 (`task deps`, `task build`, `task test:unit` all passing) and posted a follow-up with what #2086/#2095 already cover, what's still missing, a proposed approach, and two design questions: a separate table or not, and retention.

**2026-11-11**

Reproduced the gap on `main` (`226a94c9`) with a failing test, pushed to my fork. Both maintainers answered: a separate `security_scans` table, written in the same transaction as `scan_reports`, cascade on record delete, store `scanner_version`, no cleanup job for now, and admin-only auth. I confirmed on the thread. I decided to ship in two PRs, table and reconciler first.

Wrong turn: my repro test asserts that `scan_reports` keeps two rows, but the agreed design keeps `scan_reports` overwriting and puts history in the new table. I kept the test on my fork as the reproduction only and left it out of the PR.

**2026-11-11**

Built layer 1 on `feat/1874-security-scans` (not committed yet): the types, the `SecurityScan` model and its DB methods, the transaction helper in `scan.go`, cascade and `AutoMigrate`, and 13 tests. Claude wrote the code; I asked for it file by file at first, then a layer at a time, and reviewed it. Decisions: column `scan_trigger` (SQL keyword), verdict copied into each history row, and `FinishScannerRun` rolling back the `scan_reports` write if its history row is missing. Then two changes after my review: a request now stays `pending` until a scanner actually starts, instead of turning `running` when the reconciler picks it up; and `DiscardScannerRun` handles scanners that turn out not to apply.

**Toolkit**

- Tool: Claude Code writing the code a file or a layer at a time while I reviewed each step, and the repo's pre-commit hook (golangci-lint through `task`).
- What it produced: layer 1 (7 files: 2 new, 5 edited) with tests, plus a whitespace-ignored diff showing `scan.go`'s logic is unchanged.
- Difficulties: edits sent through `wsl` with a heredoc silently didn't apply once (the linter output stayed the same, which is how I caught it); the pre-commit hook needs Go and Task on the PATH; and a test fake implements the whole database interface by hand, so new methods broke its compile until I added stubs.
- What changed: the edits now go through script files instead of heredocs, I export the PATH in every WSL command, and I wrapped errors the way the linter asked.

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

- [agntcy/dir README, Development section](https://github.com/agntcy/dir#development): the `task deps`, `task build` and `task test:unit` commands I set the project up with.
- [agntcy/dir CONTRIBUTING.md](https://github.com/agntcy/dir/blob/main/CONTRIBUTING.md): the DCO sign-off rule (`git commit -s`), tests required for new behavior, and the ~10-day review window.
- [Issue #1874 thread](https://github.com/agntcy/dir/issues/1874): akijakya's [answer to my design questions](https://github.com/agntcy/dir/issues/1874#issuecomment-6795743395) and ramizpolic's [follow-up](https://github.com/agntcy/dir/issues/1874#issuecomment-6797562597) settled the design.
- [Issue #2086](https://github.com/agntcy/dir/issues/2086) and [PR #2095](https://github.com/agntcy/dir/pull/2095): showed what had already been done for scan outcomes, and how `scan_reports` got its status columns.
- The repo's own code as examples: `server/database/gorm/scan_test.go` (test helpers), `migrations/003_record_fk_on_delete_cascade.go` and `record.go` (how cascades are declared), and `server/types/signature.go` (the `interfacebloat` exemption).
