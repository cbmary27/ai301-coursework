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

**Unit 6: Installed the voice guard and wrote the Upstream section of my voice guide**

I moved my voice guide to `~/.claude/voice-guard/`, added Upstream rules for claims, questions and pings (using my own vague nomnom comment as a "Wrong" example and my agntcy follow-up as a "Right" one), and merged the guard's PreToolUse hook into my Claude Code settings. Two things broke on Windows: `python3` is only the Microsoft Store placeholder there, so the hook would have failed silently until I changed its command to `python`; and Git Bash's `ln -s` makes copies instead of links, so I used the one-line pointer files in each skill instead. The bigger shortfall was timing: I posted my claim on agntcy/dir#1874 before the guard existed, so it never checked my claim before it went up; checking the posted text afterwards is the honest version of that step, and it hasn't been run yet. My repo memory file (`CLAUDE.local.md` in my agntcy clone) is not written yet as of 2026-11-10.

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

[What a stranger would need to stand this up: your operating system,
the relevant versions (language, runtime, package manager, the project
itself), and how you set the project up. Then the challenges you faced
and how you solved them, or that none came up.]

**Steps to Reproduce**

1. [Step 1]
2. [Step 2]
3. [Observed result]

**Reproduction Evidence**

- **Commit showing reproduction:** [link to commit in your fork]
- **Screenshots/logs:** [if applicable]
- **My findings:** [what you discovered during reproduction; an
  honest, evidenced cannot-reproduce that led you to re-pick or ask
  the maintainer belongs here and costs you nothing]

**Toolkit**

- Tool:
- What it produced:
- Difficulties:
- What changed:

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
