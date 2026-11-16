# Adding Persistent Security Scan History to agntcy/dir

## Overview

[agntcy/dir](https://github.com/agntcy/dir) is an open-source directory of AI agents that security-scans registered agents. I worked on [issue #1874](https://github.com/agntcy/dir/issues/1874), which addressed a limitation where every new scan overwrote the previous result, leaving no history, no pending/running state, and no API to request a scan. I implemented a `security_scans` history table, updated the reconciler to record every scanner execution, and added admin-only `NewScan` and `ListScans` API endpoints. I also used two tools from my course toolkit: plan-check, where I wrote the rubric and grading procedure, and the course's ship-gate, where I wrote the validation manifest and the PR precheck rubric it runs. {TBA: the pull request link and where it stands today.}

## What happened

### 1. Establishing the design

On November 8, 2026, I claimed issue #1874. The following day, I followed up after investigating related issues #2086 and #2095, outlining what was already implemented, what was missing, and a proposed approach. I also raised two design questions with the maintainers.

On November 11, both maintainers agreed with the proposal:

> "A separate table sounds right to me. I'd keep `scan_reports` as it is: one row per `(record_cid, scanner_type)` holding the current state, since search filters, policy facts and the rescan scheduler all read it that way." — akijakya

> "Nicely summarized @cbmary27 @akijakya, sounds like a good plan! I would only suggest not to delete any historical scans (no cleanup job for the start). … Do note that this is an Admin API, so default config auth rules need to be patched as well." — ramizpolic

This established the core design: preserve `scan_reports` as the current-state table and introduce a separate table for historical executions, without initially deleting old records.

### 2. Reproducing the problem

Before implementing the fix, I wrote a regression test on the original `main` branch. It executed two scans against the same record: the first failed, and the second succeeded. The expected result was two inspectable executions.

Instead, only the latest result remained:

```text
scan_reports row: status=completed failure_reason="" consecutive_failures=0
Error: "[{... MCP true NONE completed ...}]" should have 2 item(s), but has 1
--- FAIL: TestRepro1874_ScanHistoryIsKept (0.01s)
```

This confirmed that the previous scan was being overwritten.

### 3. Implementing the fix

I implemented the changes in three layers:

- **Storage:** Added `security_scans` to preserve individual scan executions.
- **Reconciliation:** Updated the reconciler to record each scanner run and track its lifecycle.
- **API:** Added `NewScan` and `ListScans` endpoints, made both admin-only in the authorizer, and documented the rule that grants them.

One important decision was keeping requested scans in `pending` until a scanner actually starts on them, so that `running` always means a scanner is at work. Because the reconciler runs as a single replica, no separate step to claim a request was needed.

After the changes, an updated version of the same test, writing the two scans the way the reconciler now does, passed:

```text
security_scans row: scan_id=scan-1 status=failed failure_reason="network" scanner_version=4.8.7
security_scans row: scan_id=scan-2 status=succeeded failure_reason="" scanner_version=4.8.7
scan_reports row: status=completed failure_reason="" consecutive_failures=0
--- PASS: TestRepro1874_ScanHistoryIsKept (0.01s)
```

Both executions were now preserved, while `scan_reports` continued to maintain a single row for the latest state.

### 4. When my own tool rejected my plan

I also used my plan-check tool, built with my own evaluation rubric and procedure, to validate the implementation plan.

On November 12, its first evaluation rejected my plan because I had listed tests without providing runnable steps or expected results:

```text
"grade": "fail"
"evidence": "plan.md has no runnable test steps or expected result"
"verdict": "reject"
```

I revised the test plan to include explicit execution steps and expected database state. The second evaluation passed:

```text
"grade": "pass"
"evidence": "… Expected: it passes, with two security_scans rows (failed with reason network, then succeeded) and still one scan_reports row"
"verdict": "accept"
```

### 5. Passing the ship-gate

On November 16, I ran the ship-gate, which runs the checks in my validation manifest and then my PR precheck rubric.

The first run rejected the branch because Git reported a 177-file diff containing unrelated release changes, UI bundles, and identity code. The cause was a stale local `main` branch and phantom changes reported by Git on Windows.

After fixing both issues, the branch passed all checks:

```text
ship-gate: PASS

Plan fidelity [pass]
Test evidence [pass]
Diff quality [pass]
Standards and comms [pass]
```

### 6. Pull request status

{TBA}

The initial implementation covers historical storage, reconciler integration, and the admin API. I have kept additional functionality separate for a follow-up PR, including client support, `dirctl scan`, recovery of scans stuck in `running`, and scan cooldowns.

## Limitations and what's next

The main limitation is that I have not yet completed an end-to-end scan through the new API. This requires SPIFFE authentication, scanner binaries, and an LLM API key. I am asking the maintainers in my pull request what level of end-to-end coverage they expect.

Additionally, manually requested scans currently wait for the existing six-hour scan interval rather than executing immediately.

The next step is to complete the initial PR review, agree on end-to-end testing requirements, and address the deferred functionality in PR 2.

The key outcome is a separation between historical scan executions and current scan state, allowing agntcy/dir to retain scan history without disrupting the existing systems that depend on `scan_reports`.