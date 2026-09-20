# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53?utm_source=chatgpt.com

**Verdict output**

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
All three are in the scoped repo (codepath/pathreview-ai301-fa26-s1). Grading each independently against rubric.md.

Shared repo evidence (applies to all three):
- Not archived; commits 2026-09-16 by Aburke225 — 3 days before today (2026-09-19), well inside 90 days. Repo
- docs/CONTRIBUTING.md has no AI ban and no maintainer-approvalgate — it says others knowyou're working on it" (a convention, not a permission gate). No AI_POLICY.mlosurerequirement. Policy ✔.                                      gh pr list --so has zero PRs, so no issue has a linked or mentioned PR.                      All three issugnees": [], andtimelines containing only label events — no claims of any   kind. (The Patssmate claimsnever even comes into play.)                                
---                                                           
Ranked read-out                                               
Accepted — 1st: #53 — PII scrubber fails to redact            renthesized US
- Open ✔ · maintainer alive ✔ · not taken ✔ · repo active ✔ · policy clear ✔
- Preferred: well-detailed pass (runnable repro with observed   output, plus finner-ideal pass(good first issue + tier-1).                                  Fit: the tighthe three — a regex fix in safety/pii_scrubber.py with the tests already written  to tell you whhris's strongestlanguage (Python), and the xfail-removal step in CONTRIBUTING makes the defious. Best firstPR of the set.                                               
Accepted — 2nd: #56 — Structural chunker silently drops         cuments with n
- All required checks pass on the same evidence.                Preferred: weltest_document_with_no_headings), beginner-ideal pass (good    first issue +
- Fit: equally beginner-labeled, but ranked second because the  body leaves a hunked as a single block or falling back to another strategy" — which you'd      have to settletly more thinkingthan #53, still well within scope.                           
Accepted — 3rd: #67 — Review creation does not verify profile   nership
- All required checks pass: OPEN, no comments/assignee/PR, same active repo an
- Preferred: well-detailed pass (names core/services/istency withget_review()/list_reviews(), and a concrete attack request —    though the bodames no failingtest). Beginner-ideal fail — no good first issue label, and     the maintaineriate difficulty;the fix requires understanding the auth dependency and the      Profile.user_i
- Fit: this is actually the closest to Chris's full-stack goal    (FastAPI routerth taking second, after one tier-1 PR has already walked the fork → xfail →       green-CI workf
                                                                One tension wort#67 because itsbeginner check is only preferred, even though the maintainer's  own tier-2 labelThat's the rubricbehaving as written — if you'd rather tier-2 issues be excluded outright, that b rubric.md, notas an override here.

[
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-
s1/issues/53",
    "checks": [
      {"name": ", "grade": "pass", "evidence": "\"state\":\"OPEN\", \"closedAt\":null, zero
comments and no
      {"name": "Maintainer is alive", "grade": "pass",
"evidence": "Abuer) committed tomain on 2026-09-16, 3 days before today"},
      {"name": "de": "pass","evidence": "Runnable repro with observed output, plus four
named failing terubber.py"},
      {"name": "Issue is not taken up", "grade": "pass",
"evidence": "asseline holds onlylabel events, and `gh pr list --state all` returns []"},
      {"name": "": "pass","evidence": "pushedAt 2026-09-16; three commits on 2026-09-16,
not archived"},
      {"name": "Issue is ideal for beginners", "grade": "pass",
"evidence": "Labtier-1' (Starterdifficulty)"},
      {"name": " "pass","evidence": "docs/CONTRIBUTING.md states no AI restriction and
no approval gatet others knowyou're working on it'"}
    ],
    "verdict": "accept"
  },
  {
    "item": "httreview-ai301-fa26-s1/issues/56",
    "checks": [
      {"name": "Issue is open and unresolved", "grade": "pass",
"evidence": "\"s:null, no comment or PR indicating a fix"},
      {"name": ": "pass","evidence": "Maintainer Aburke225 committed to main on
2026-09-16, with
      {"name": "Issue is well detailed", "grade": "pass",
"evidence": "Pyt0' plus thefailing test test_document_with_no_headings"},
      {"name": "e": "pass","evidence": "No assignee, no comments, timeline is label events
only, repo has z
      {"name": "Repository is active", "grade": "pass",
"evidence": "Latted 2026-09-16, 3days ago"},
      {"name": ", "grade": "pass", "evidence": "Labeled 'good first issue' and 'tier-1'"},
      {"name": " "pass","evidence": "No AI_POLICY file; CONTRIBUTING.md and PR template
impose only CI/spproval"}
    ],
    "verdict": "
  },
  {
    "item": "https://github.com/codepath/pathreview-ai301-fa26-
s1/issues/67",
    "checks": [
      {"name": ", "grade": "pass", "evidence": "\"state\":\"OPEN\", \"closedAt\":null, no comments and no
      {"name": "Maintainer is alive", "grade": "pass",        "evidence": "Maio main on2026-09-16, within 90 days"},                                       {"name": "de": "pass","evidence": "Names core/services/review_service.py, contrasts with get_review( concrete POST/reviews example"},                                                 {"name": "e": "pass","evidence": "assignees: [], comments: [], timeline shows only 'bug' and 'tier- all"},
      {"name": "Repository is active", "grade": "pass", "evidence": "pusd"},
      {"name": "Issue is ideal for beginners", "grade": "fail",
"evidence": "No ntainer labeledit 'tier-2' (Intermediate difficulty) and the fix needs the
auth + Profile.u
      {"name": "Policy Restriction", "grade": "pass",
"evidence": "doc AI-contributionban and no maintainer approval requirement to claim an issue"}
    ],
    "verdict": "accept"
  }
]
```
---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

agreement: 8/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in claimed, policy) 

agreement: 16/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in policy)

agreement: 19/20 scored items  (bar: 18/20: PASS)

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

id: issue-10 
issue-10  rubric's decision: reject  gold standard: reject
Reasoning: The repository and the maintainer is active, the issue is well detailed and is not claimed. But the important indicator to why it was rejected is because of the expression of interest in the discussion/comment section of the issue. Hence, the issue was rejected.    

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]

| Issue is not taken up | Check if someone has already taken up the issue | no assignee, no linked/mentioned PR, no blocking claim. Check the discussion/comment section of the issue to see if anyone has been RECENTLY working on it or has shown any expression of interest (within the last 6 months) regardless of whether there is no assignee. If any of the discussions indicate that the issue has been informally resolved or closed, then block the issue.| required |

Reasoning: This check was revised during calibration because an old expression of interest was incorrectly treated as evidence that an issue was currently taken up. The current wording focuses on recent activity rather than stale claims, while still blocking issues with an assignee, PR, recent expression of interest, or evidence that the issue has been informally resolved or closed. This makes the check distinguish between an active claim from a stale one.

**Trade-offs**

This check may accept an issue where someone expressed interest in the past but has not worked on it recently. Issue #09 showed this trade-off: it had an old expression of interest, but there was no recent activity, assignee, or active PR. The revised check treats stale claims as non-blocking so that abandoned claims do not prevent an issue from being selected.

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.

- Since this is my first time contributing to open-source, I wanted to work on something labelled as a 'good first issue' while also being something I was familiar with. I provided a three issue links in live mode, a mix of tier 1 and tier 2 issues. Issue 53 details a parsing error with the telephone number field. This is related to a project I worked on before for an internship, developing a parser to scan through payment documents to extract relevant fields.

The issue also has a focused scope: the existing pattern needs to be updated to handle parenthesized US phone numbers, and the relevant tests are already identified. This makes the issue manageable within the time available for my first open-source contribution while giving me an opportunity to apply experience I already have with parsing and regular expressions!

2. What the verdict identified correctly, and what you weighed that the rubric could
   not.

- The verdict correctly identified that issue #53 is open, not currently taken up, and in an active repository. Beyond what the rubric evaluated, I checked whether the issue matched my previous experience and interests. The issue involves parsing telephone numbers and updating a regular expression, which connects to my previous internship experience developing parsers for payment documents.

3. The anticipated difficulty in claiming it.]

- This is a relatively easy issue to fix, so might be a bit difficult to claim it if not done early! I hope I can claim it, but if not, I have two other issues that I can select!

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
