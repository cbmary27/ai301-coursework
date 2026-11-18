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
**Pull Request:** https://github.com/agntcy/dir/pull/2514

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

I installed the scout over my Unit 1 skill, rewrote my fit profile around good first issues and small bugs in Python, Java, Go and Kotlin, and wrote six `gh search issues` queries plus ranking rules (drop assigned, stale or long-thread issues, one per repo, bugs first, fewest comments). 

The first scan pulled 558 unique issues and graded the top 5, but "fewest comments first" mostly surfaced issues opened that same day in brand-new repos with 0-28 stars, often filed by the maintainers' own AI agents. 

My rubric passed them because it has no adoption check, and the ranking let K1rL3s/maxo#388 through with a fixing PR already open, since search results don't carry cross-references (the rubric's "not taken up" check caught it). I logged both gaps in scan-notes.md rather than patching blindly, and took my real picks from the Issue Selection site.

**Unit 6: Installed the voice guard, wrote my Upstream voice rules, and gave Claude a memory file for agntcy/dir**

I added Upstream rules for claims, questions and pings to my voice guide (my vague nomnom comment became a "Wrong" example) and wired the guard in as a Claude Code hook. On Windows that broke twice: `python3` is only a Microsoft Store placeholder, so I changed the hook to call `python`, and Git Bash's `ln -s` silently makes copies, so I used one-line pointer files instead. My claim on #1874 was posted before the guard existed, so I ran the guard's manual check on it afterwards: it stopped my 2026-11-08 comment on my own rule "A claim names my first step and when I'll report back", and repro-check rejected it as not specific to the issue. Only my 2026-11-09 follow-up made the claim pass. While doing that I found that my installed repro-check had been grading with my Unit 3 plan-check rubric, so I restored my Unit 2 rubric from `tools/repro-check/`. I also wrote `CLAUDE.local.md` in my clone (DCO sign-off, the scan subsystem's 4 key files, the exact build and test commands, and the WSL PATH fix Go and Task need), kept out of git with `.git/info/exclude`.

**Unit 7: Installed the ship-gate and wrote a manifest for agntcy/dir's two CI checks**

My clone and its Go toolchain live in WSL, but Claude Code, my skills and the voice guard are on Windows, so I ran the gate on Windows against `\\wsl.localhost\Ubuntu\home\chris27\dir`. That fought me three times: Windows git refused the clone as "dubious ownership" until I added it to `safe.directory`, the installed hook called `python3` (the Microsoft Store placeholder again) so I changed it to `python`, and the manifest's commands have to call into WSL (`wsl -e bash -lc "... cd ~/dir && task test:unit"`), because the gate runs them in a fresh Windows shell. My manifest has the two checks the repo's CI runs, `task test:unit` and `task lint`, and I tested both exactly as the gate runs them: exit 0, no failing package, 0 lint issues (lint takes about 6 minutes). I also found that both of my hooks only watch Claude Code's Bash tool, so on Windows a PR opened through the PowerShell tool would skip them. For the hook test I ran `gh pr create --help` through Bash: the ship-gate stopped it because no fresh pass existed, and the voice guard stopped it too because a `--help` call has no body to read (my voice-guard log records its stop at 16:04 on 2026-11-16). The gate's first real run on my branch on 2026-11-16 stopped me: it saw a 177-file diff full of release, UI and identity changes, because my local `main` was stale and Windows git was reporting line-ending and file-mode changes that weren't real. I reset `main` to `origin/main`, set `core.autocrlf=false` and `core.filemode=false` in the clone, re-ran my tests on the committed head, and the second run passed. That pass also flagged six new files committed as executable, which I fixed in a small commit. On 2026-11-18 I rebased onto the latest `main` and ran the gate again; it passed at 17:50 (unit tests in 11s, lint in 530s, all four precheck criteria passing). I then opened the PR myself in the browser at 17:56 as a draft, so the gate hook didn't see the open itself, and I made a few small wording edits to the description while opening it.

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
- `proto/agntcy/dir/security/v1/` and the generated `api/security/v1/`: the security API, which has the `ScanReport` message but no service to start or list scans
- `server/controller/` and `server/server.go`: where each gRPC service is implemented and registered
- `server/authz/authorizer.go`: decides who may call each method; an admin-only API has to be added to `identityOnlyMethods` so a trust-domain-wide rule can't grant it
- Later, for PR 2: `utils/scanner/mcp.go` (`merge()` drops the scanner version), `client/scan.go` and `cli/cmd/` for a `dirctl scan` command

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

The work is split into two PRs. **PR 1 (this story)** is the simplest version of the whole feature: the table, the reconciler recording history and running manual scans, and the `NewScan`/`ListScans` Admin API with its admin-only auth rule. **PR 2** hardens it: the Go client and `dirctl scan` commands, recovery of scans left `running` after a crash, a cooldown on repeated requests, a faster loop for manual scans, and carrying the MCP scanner's version through `merge()`.

Deliberately not changing: what `scan_reports` means or how it's written (same rows, same retry schedule), scheduling, search filters, policy facts, ingest of peers' reports, and the scanner interface. No retention or cleanup job (ramizpolic asked for that to be a separate issue). Selecting a single scanner in `NewScan` is left out; the issue only asks for a CID.

**Implementation Plan**

PR 1, layer 1 (storage):

1. `server/types/database.go`: progress statuses, triggers, the `not-applicable` failure reason, the `SecurityScanObject` interface, and a `SecurityScanDatabaseAPI` interface added to `DatabaseAPI`.
2. New `server/database/gorm/security_scan.go`: the `SecurityScan` model with indexes, and the methods `CreatePendingScan` (returns the scan already pending or running instead of queueing another), `ListPendingScans`, `StartScannerRun`, `FinishScannerRun`, `DiscardScannerRun`, `CloseScanPlaceholder` and `ListScans`.
3. `server/database/gorm/scan.go`: move `UpsertScanReport`'s logic, unchanged, into a helper that runs inside the caller's transaction.
4. `record.go`: add `SecurityScans` with `OnDelete:CASCADE`. `migration.go`: add `SecurityScan{}` to `AutoMigrate`. A new table needs no numbered migration.
5. Tests in `security_scan_test.go`, plus no-op stubs in `reconciler/tasks/signature/task_test.go`, whose fake implements the whole database interface by hand.

PR 1, layer 2 (reconciler):

6. `reconciler/tasks/scan/task.go`: run pending manual scans first, then the scheduled pass under one `scan_id`, skipping records just scanned manually. Wrap each scanner run in `StartScannerRun` → `FinishScannerRun` (or `DiscardScannerRun` if it didn't apply), and close a manual scan's placeholder when no scanner took it. History is best effort: if a history write fails, `scan_reports` is still written exactly as before.
7. Reconciler tests with a fake DB, store and runners.

PR 1, layer 3 (API):

8. New `proto/agntcy/dir/security/v1/scan_service.proto`: `ScanService` with `NewScan` and a streamed `ListScans`, a `Scan` message mirroring a history row, and `ScanStatus`/`ScanTrigger` enums. Go code generated with the repo's `buf generate`.
9. New `server/controller/scan.go`: validates the CID, returns NotFound for a record this node hasn't indexed, queues the scan under the caller's SPIFFE ID, and maps rows to the proto.
10. `server/server.go`: register the service only when authorization is enabled, like the policy audit service. `server/authz/authorizer.go`: add both methods to `identityOnlyMethods`, so only a rule naming an admin's SPIFFE ID grants them, never a whole trust domain. README entry and an authz test.

Test plan (run in WSL, from `~/dir` unless noted):

1. **Reproduction, before.** On my repro branch (`~/dir-repro`, commit `4221fc50`, based on `main`): `cd server && go test ./database/gorm/ -run TestRepro1874 -v -count=1`. Two scans of one record by the MCP scanner, failed with reason `network` and then completed. Expected on `main`: the test fails with "should have 2 item(s), but has 1", because one `scan_reports` row is left and the failure is gone.
2. **Reproduction, after.** The same two scans on `feat/1874-security-scans`, written the way the reconciler now writes them (`StartScannerRun` then `FinishScannerRun` for each), as a temporary copy of the repro test that isn't committed: `cd server && go test ./database/gorm/ -run TestRepro1874 -v -count=1`. Expected: it passes, with **two** `security_scans` rows (`failed` with reason `network`, then `succeeded`) and **still one** `scan_reports` row holding the latest result. That shows history is kept while the current-state table works as before.
3. **Storage tests.** `cd server && go test ./database/gorm/ -count=1`. Expected: the new `security_scan_test.go` tests pass, including `TestFinishScannerRun_KeepsHistoryWhileScanReportsOverwrites` (the permanent version of step 2) and `TestSecurityScans_DeletedWithRecord` (cascade), and every existing scan test still passes. `git diff -w main -- server/database/gorm/scan.go` shows only the function split.
4. **Reconciler tests.** `cd reconciler && go test ./tasks/scan/ -count=1`. Expected: the `TestRun_*` tests pass, showing a scheduled pass writes history under one `scan_id`, a scanner that doesn't apply leaves no row, a manual scan runs once before the scheduled pass, and `scan_reports` is still written when a history write fails.
5. **API and auth tests.** `cd server && go test ./controller/ ./authz/ -count=1`. Expected: the `TestScan_*` controller tests and `TestAuthorize_ScanServiceNeedsAdminIdentity` pass. That shows a scan is queued under the caller's identity, a bad or unindexed CID is rejected, and only a rule naming the admin grants the methods.
6. **The repo's own checks.** `task test:unit` and `task lint`, as CI runs them. Expected: exit code 0 for both, with no failing package and 0 lint issues.
7. **End to end: not done in this PR.** A real run needs authorization with SPIFFE identities, the scanner binaries and an LLM key (see the deviation below). I'll ask the maintainers in the PR which coverage they want.

Deviations so far:

- **Two PRs instead of one** (2026-11-11), so the schema gets reviewed before the API is built on it.
- **Column `scan_trigger` instead of `trigger`**, because `TRIGGER` is an SQL keyword and this package writes raw `Where` strings.
- **No "claim" step for pending scans** (2026-11-11). My first version flipped a request to `running` as soon as the reconciler picked it up, before any scanner ran. I changed it so a request stays `pending` until its first scanner starts, which keeps `running` meaning one thing everywhere. That's safe because the reconciler runs as a single replica (`replicas: 1`) and never overlaps its own runs.
- **Added `DiscardScannerRun`** (2026-11-11). Scanners only find out they don't apply to a record after they've run, so the row created when they start has to be removed, or handed back as the placeholder, when they don't apply.
- **Changed the PR split** (2026-11-12). Originally PR 1 was the table and reconciler, and the API came in PR 2. That left a table nobody could ask to scan, and `CreatePendingScan` with no caller. PR 1 is now the simplest version of the whole feature, API included, and PR 2 is hardening and the client side.
- **Moved the cooldown and stuck-scan recovery to PR 2** (2026-11-12). Both were built and tested, but neither is needed for the feature to work: dedup of pending/running scans covers repeated requests, and a scan left `running` only happens if the reconciler crashes mid-scan. Taking them out kept PR 1 smaller.
- **Manual scans wait for the scan task's interval** (2026-11-12). They run at the start of the existing scan pass, every 6 hours by default. A faster loop is planned for PR 2, and I'll ask the maintainers in the PR which they prefer.
- **No end-to-end run yet** (2026-11-12). My testing plan included one real run with the scanners installed. I haven't done it: a real run of `NewScan`/`ListScans` needs authentication and authorization (SPIFFE identities, so SPIRE in practice), because the service is only offered with authorization on, and the repo's no-cluster e2e suites don't enable auth. A run with the real scanners needs the Cisco scanner binaries, and the MCP source scan needs an LLM key. A full deployment would also need Docker in WSL for a kind cluster. The scheduled half could be shown on a local `dirctl daemon` with the scanners installed. I'm asking the maintainers in the PR review which end-to-end coverage they want, and the PR lists it as not done.

**Toolkit**

- Tool: the issue thread with the maintainers and Claude Code reading the reconciler and scanner code to shape the design; then my Unit 3 plan-check, run on this section copied into `plan.md` plus a short `plan-comment.md` in my clone (never posted).
- What it produced: the agreed design, the PR split and the file list above. plan-check's first run rejected the plan: Diagnosis and Scope passed, but Test failed because `plan.md` only listed test files to add, with no commands or expected result, and the comment said "rerun my reproduction" without saying what result proves the fix. After I added the Test plan above and the expected result to the comment, the second run accepted it.
- Difficulties: the thread left open what a pending row is, and the scanner interface only has `Name()` and `Run()`, so a scanner can't say it doesn't apply until it has run. On the tool side, my procedure says to take the reproduction from a posted repro comment, and mine was never posted (it lives on my fork), so plan-check had to grade against the reproduction the drafts quote, a case my procedure doesn't cover. My real test plan was in Testing Strategy, which `plan.md` doesn't include, and that's what made the first run fail.
- What changed: the placeholder-takeover design, `DiscardScannerRun`, keeping requests `pending` until a scanner starts, and moving the API into PR 1 with the cooldown and stuck-scan recovery moved out, all recorded as deviations above. I added the Test plan to this section so `plan.md` carries it. I'd add a step to my procedure for a reproduction that is quoted in the drafts but not posted.

---

## Testing Strategy

**Reproduction, before and after.** Before (on my repro branch, `4221fc50`): two scans of the same record and scanner, failed then completed, leave one `scan_reports` row and no history anywhere, so the test fails with "should have 2 item(s), but has 1". After (on `feat/1874-security-scans`): the same two scans, written the way the reconciler now writes them, leave **two** `security_scans` rows (`failed` with reason `network`, then `succeeded`, both with scanner version `4.8.7`) **and still one** `scan_reports` row with the latest result, and the test passes. I ran the "after" as a temporary copy of the repro test on my branch and removed it; it isn't part of the PR. The same behavior is covered permanently by `TestFinishScannerRun_KeepsHistoryWhileScanReportsOverwrites`.

**Storage (layer 1), done.** 13 unit tests in `server/database/gorm/security_scan_test.go`, on in-memory SQLite like the repo's existing scan tests. They cover history kept while `scan_reports` still overwrites, the verdict and scanner version copied, a failed write rolling back the `scan_reports` upsert, dedup in `CreatePendingScan`, `ListPendingScans` changing nothing, placeholder takeover, discarding a scanner that didn't apply (deleted, or handed back as the placeholder), closing an unused placeholder, list order/filter/paging, and cascade on record delete. Command: `cd server && go test ./database/gorm/ -count=1`.

**Nothing existing changed.** The existing scan, upsert, scheduling and cascade tests still pass, and `git diff -w server/database/gorm/scan.go` shows only the function split, no logic change.

**Reconciler (layer 2), done.** 5 tests in `reconciler/tasks/scan/history_test.go` with a fake DB, store and runners: a scheduled pass writing history under one `scan_id` (finished for scanners that ran, discarded for one that didn't apply), `scan_reports` still written when a history write fails, a manual scan running first and only once, a manual scan whose record can't be pulled, and a manual scan no scanner applies to.

**API (layer 3), done.** 6 tests in `server/controller/scan_test.go`: a scan queued under the caller's identity, an existing scan returned instead of a duplicate, bad and unindexed CIDs rejected before anything is queued, database errors returned without their detail, the field mapping, and the status filter and paging. Plus `TestAuthorize_ScanServiceNeedsAdminIdentity`: only a rule naming the admin grants the methods, not the node's own trust domain, an auditor or a peer.

**The repo's own checks.** `task test:unit` and `task lint` (golangci-lint per module, buf and helm), the two checks the repo's CI runs, must pass. They're the two rows of my ship-gate manifest, and both pass on my branch.

**End to end, deferred.** Not done, and listed as not done in the PR (see the deviation in Solution Approach). It would need auth with SPIFFE identities for the API, the scanner binaries plus an LLM key for real scans, and Docker for a cluster. I'm asking the maintainers in the PR which coverage they want: an in-process integration test, a local daemon run with the real scanners, or something in `tests/e2e`.

**Toolkit**

- Tool: `go test` on in-memory SQLite, the repo's golangci-lint through its pre-commit hook, and `task test:unit`.
- What it produced: 24 new tests across the three layers plus one authz test, all passing; 0 lint issues in `server` and `reconciler`; a full `task test:unit` pass (107 packages ok) on the finished PR 1 code; and before/after output of my reproduction.
- Difficulties: the first lint run found 4 issues in my code (3 unwrapped errors and a 17-method interface), and a later one flagged a test as too complex. Unit tests can't exercise the real scanners or the auth stack.
- What changed: I wrapped the errors and exempted the interface with `//nolint:interfacebloat`, following the repo's own precedent in `server/types/signature.go`, and split the complex test with a helper. I planned an end-to-end run, then deferred it once I saw what it needs, and I'm asking the maintainers which coverage they want.

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

Built layer 1 on `feat/1874-security-scans` (not committed yet): the types, the `SecurityScan` model and its DB methods, the transaction helper in `scan.go`, cascade and `AutoMigrate`, and 13 tests. Decisions: column `scan_trigger` (SQL keyword), verdict copied into each history row, and `FinishScannerRun` rolling back the `scan_reports` write if its history row is missing. Then two changes after my review: a request now stays `pending` until a scanner actually starts, instead of turning `running` when the reconciler picks it up; and `DiscardScannerRun` handles scanners that turn out not to apply.

**2026-11-12**

Committed the model and database API (`9e17f517`) and pushed the branch to my fork. Changed the PR split: PR 1 is now the simplest version of the whole feature, so I took the cooldown and stuck-scan recovery out (PR 2) and built the rest. Layer 2: the reconciler runs pending manual scans before the scheduled pass and writes history around every scanner run, with `scan_reports` written as before if a history write fails. Layer 3: `scan_service.proto` with `NewScan` and `ListScans`, its generated code, the controller, registration only when authorization is enabled, and both methods made identity-only in the authorizer. Full `task test:unit` passes (107 packages ok) and lint is clean. Reran my reproduction on the branch: two history rows and one `scan_reports` row, where `main` had one row and no history. Didn't do the end-to-end run; it needs auth, the scanner binaries and an LLM key, so I'll ask in the PR what coverage the maintainers want.

Wrong turn: I first assumed the pre-commit hook linted my whole working copy, so I committed two files on their own. The hook stashes unstaged files, so it saw `security_scan.go` without the `scan.go` helper it calls and failed the typecheck. I added `scan.go` to that commit.

**Toolkit**

- Tool: I used Claude Code assisstance in writing the code for a file or a layer at a time while I reviewed each step and led the design decisions, and the repo's pre-commit hook (golangci-lint through `task`).
- produced: layer 1 (7 files: 2 new, 5 edited) with tests, plus a whitespace-ignored diff showing `scan.go`'s logic is unchanged.
- Difficulties: edits sent through `wsl` with a heredoc silently didn't apply once (the linter output stayed the same, which is how I caught it); the pre-commit hook needs Go and Task on the PATH; and a test fake implements the whole database interface by hand, so new methods broke its compile until I added stubs.
- What changed: the edits now go through script files instead of heredocs, I export the PATH in every WSL command, and I wrapped errors the way the linter asked.

---

## Pull Request

**PR Link:** https://github.com/agntcy/dir/pull/2514 (draft, opened 2026-11-18, title `feat(dir): add security scan history and admin scan API`, `Refs #1874`)

**PR Description:** The PR is the first of two for #1874 and follows the design agreed on the issue. It says up front that it isn't ready to merge until the maintainers answer my questions. Its key changes are the `security_scans` history table (one row per scanner run, with status, trigger, scanner version and who asked, written in the same transaction as `scan_reports`), the reconciler recording history and running pending manual scans first, the admin-only `ScanService` with `NewScan` and `ListScans`, and the auth rule documented in the authz README, with the Helm default left unchanged and an offer to add an example. It walks through how a manual scan flows in four steps, lists the key files, and lists what's planned for the follow-up PR (client and `dirctl scan`, stuck-scan recovery and a cooldown, a faster manual loop, and keeping the MCP scanner's version). Testing covers the before/after reproduction and 25 new unit tests, with `task test:unit` and `task lint` passing, and says plainly what isn't tested yet: real scanner binaries, a running server with auth, and Postgres. It asks two questions: what end-to-end coverage they'd like, and whether manual scans can wait for the scan interval until the follow-up. It ends with an AI-use note.

**Maintainer Feedback:**

- 2026-11-18: none yet. The only comment so far is the repo's size bot, which flagged the PR as over 2,000 lines and asked me to make sure it addresses one issue. I replied that 942 of the lines are generated by `buf` from the new proto and about 970 are tests, that it covers only #1874, and that the client, `dirctl scan`, stuck-scan recovery and the cooldown are already split into a follow-up PR.
- The repo's automated checks (PR title, DCO, label) passed.

**Status:** Awaiting review (draft, waiting on answers to my two questions).

**Toolkit**

- Tool: the ship-gate, running my two-check manifest (`task test:unit` and `task lint` through WSL) and then my pr-precheck rubric on the branch, title and description. I also used Claude Code to help trim the description and check its claims against the code.
- What it produced: a stop on the first run (a 177-file diff from a stale local `main` and phantom Windows git changes), then passes on 2026-11-16 and again on the rebased branch on 2026-11-18, with notes such as the six files committed as executable, a missing sentence about the Helm default the maintainer had asked about, and questions that didn't say what I had already checked.
- Difficulties: the gate runs on Windows against my WSL clone, so Windows git needed `safe.directory`, `core.autocrlf=false` and `core.filemode=false` before its diff matched reality; lint took 18 minutes on one run; a pass expires after 30 minutes and covers only the exact branch and description it checked, so rebasing meant running it again; and its hook only sees PRs opened through Claude Code's Bash tool, so opening in the browser skipped it.
- What changed: I fixed the file modes in a separate commit, added the Helm sentence and a manual-scan walkthrough to the description, rebased and re-ran the gate before opening, and opened the PR as a draft. Next time I would make every description edit before the final gate run, so the posted text matches what was checked exactly.

---

## Learnings and Reflections

**Technical Skills Gained**

- **How an AI agent directory works.** agntcy/dir is like a package registry for AI agents: each agent, MCP server or skill is published as a record described in the OASF format and identified by a CID (a hash of its content). Nodes share records over a peer-to-peer network, so a record can arrive from someone else's node, and records can be signed and verified so you know who published them.
- **How the directory keeps those records trustworthy through scans.** A background process, the reconciler, runs Cisco AI Defense's MCP, Skill and A2A scanners over the stored records on an interval, and rescans when a result is older than its TTL or a failed scan's retry is due. The verdict goes into `scan_reports`, which search filters, policies and scheduling all read as "the current state", which is exactly why history couldn't just be added to that table and needed its own.
- **Go and GORM for real.** Keeping two tables consistent with a single transaction (`gormDB.Transaction`) and moving existing logic into a helper that runs inside the caller's transaction without changing it; declaring `ON DELETE CASCADE` through a model relation; and learning that a brand-new table only needs `AutoMigrate`, while numbered migration files are for changing tables that already exist.
- **Testing in a large codebase.** Writing table-level tests against in-memory SQLite with the repo's own helpers, using `git diff -w` to prove a refactor only moved code, and running the repo's golangci-lint through its pre-commit hook, which caught unwrapped errors and an oversized interface in my code.
- **Open-source workflow.** Forking and pushing branches to my fork instead of upstream, DCO sign-off on every commit, conventional PR titles, git worktrees to keep a reproduction separate from the real branch, and working in WSL because the project's tooling expects Linux.

**Challenges Overcome**

- **My own tools rejected my work.** My scout first rejected #1874 because its claim check couldn't tell a released claim from a live one, and later the voice guard and repro-check both rejected my first claim comment as too generic. I fixed the rubric for the first, and I owned the second: only my follow-up comment, with specifics and two design questions, made the claim pass.
- **A tool graded with the wrong rubric.** Partway through Unit 6 I found my installed repro-check had been using my Unit 3 plan-check rubric. I only noticed because its checks talked about "plans" while I was grading a claim. I restored my Unit 2 rubric from my course repo.
- **An open design question nobody had answered yet.** The thread settled the table, but not what a pending manual scan is when only the reconciler knows which scanners apply. Then I spotted that my first version marked a scan `running` before any scanner had run. Reading the reconciler's code (one replica, runs never overlap) showed the "claim" step wasn't needed, so a request now stays `pending` until a scanner actually starts.
- **Environment traps.** On Windows the voice-guard hook needed `python` instead of `python3`; in WSL, Go and Task weren't on the PATH for non-interactive shells; and edits sent through `wsl` with a heredoc silently didn't apply. I caught that one only because the linter output didn't change.

**What I'd Do Differently Next Time**

- **Check the claim before posting it.** I posted my claim before my voice guard existed, and it failed my own rules afterwards. Next time the claim goes through my checks first, and names the issue's specifics and when I'll report back.
- **Ask the design questions in the claim.** My two numbered questions got answers from two maintainers within two days, which unblocked everything. I'd ask them even earlier next time, since the difficulty note had already flagged the open edges.
- **Verify a tool's files after installing it.** The repro-check mix-up would have been a one-minute check right after Unit 3.
- **Check git identity before the first commit** in a new repo, instead of trusting my global config.
- **Size the issue honestly up front.** #1874 is bigger than a typical first issue. Splitting it into two PRs worked, but I'd plan that split from the start instead of deciding it once the design was settled.

---

## Resources Used

- [agntcy/dir README, Development section](https://github.com/agntcy/dir#development): the `task deps`, `task build` and `task test:unit` commands I set the project up with.
- [agntcy/dir CONTRIBUTING.md](https://github.com/agntcy/dir/blob/main/CONTRIBUTING.md): the DCO sign-off rule (`git commit -s`), tests required for new behavior, and the ~10-day review window.
- [Issue #1874 thread](https://github.com/agntcy/dir/issues/1874): akijakya's [answer to my design questions](https://github.com/agntcy/dir/issues/1874#issuecomment-6795743395) and ramizpolic's [follow-up](https://github.com/agntcy/dir/issues/1874#issuecomment-6797562597) settled the design.
- [Issue #2086](https://github.com/agntcy/dir/issues/2086) and [PR #2095](https://github.com/agntcy/dir/pull/2095): showed what had already been done for scan outcomes, and how `scan_reports` got its status columns.
- The repo's own code as examples: `server/database/gorm/scan_test.go` (test helpers), `migrations/003_record_fk_on_delete_cascade.go` and `record.go` (how cascades are declared), and `server/types/signature.go` (the `interfacebloat` exemption).
