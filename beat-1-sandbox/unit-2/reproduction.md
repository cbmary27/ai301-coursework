# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

cbmary27

[Your GitHub username, exactly as it appears on your profile — no `@`, no profile URL. Your
comments upstream are identified by this name.]

---

## Posted upstream

**Claim comment**

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5849220232

Hi! I'd like to work on the issue described in #53. This is my first time contributing to this repository. I'll reproduce the behavior locally and reply to this thread with a reproduction report, including the environment I test on, since the issue doesn't state one before proposing any change.

**Reproduction comment**

[Link to the comment where you posted your reproduction. It must record the environment
(OS, relevant versions, code state), steps a stranger could follow, and what you observed.
**Then paste the text of that comment underneath the link** — the pasted text is what this
field is graded on, so copy across what you actually posted.]

Link: https://github.com/codepath/pathreview-ai301-fa26-s1/issues/53#issuecomment-5856700497

Continuing on this. Here's my Reproduction Report

1. Project Setup
I followed the environment requirements as stated in docs/SETUP.md. All commands were run on Git Bash terminal

Operating System - Windows 11

Environment: (All satisfy the minimum version listed in SETUP.md)

Git - 2.55.0.windows.3
Python - 3.13.13
Node.js - 24.14.0
npm - 11.9.0
Docker - 29.8.0
Docker Compose - v5.5.1

*Node.js, npm, Docker, and Docker Compose are not required for reproducing this specific issue, but are installed for future development.

2. Issue Reproduction
The PIIScrubber functionality can be tested without running the full application setup or make setup, since this issue is isolated to pii_scrubber.py. I created a small reproduction script containing the following code:

from safety.pii_scrubber import PIIScrubber
s = PIIScrubber()
print(s.scrub('Call me at (555) 123-4567 or 555-123-4567'))
# observed: 'Call me at (555) 123-4567 or [REDACTED]'
print(s.detect('Call me at (555) 123-4567'))
# observed: []
Creating, activating a Python virtual environment and downloading any necessary imports:

python -m venv .venv
source .venv/Scripts/activate
pip install structlog pytest
To run the test:

PYTHONPATH=. python claim_draft/test_PII.py
*Note: I created a temporary reproduction script named test_PII.py under a folder 'claim_draft' in the repository root for this reproduction. This is not an existing repository folder/file.

Result:

Call me at (555) 123-4567 or [REDACTED]
2026-09-26 18:16:16 [info     ] pii_detected                   count=0 types=0
[]
(.venv)
Running all the extra tests listed in the issue:

pytest -q tests/unit/test_pii_scrubber.py -k "test_us_phone_number_redaction or test_us_phone_formats or test_detect_phone_pii or test_phone_at_start_of_text"
Result:

xxxx                                                                                                                                                                   [100%]
21 deselected, 4 xfailed in 1.27s
The output matches the behavior described in the issue:

(555) 123-4567 remains unredacted
555-123-4567 is redacted
detect() returns an empty list for (555) 123-4567

The expected result is that the test input, (555) 123-4567, should be redacted, the same way the other test input is redacted.

3. Analysis and Proposed Solution
After testing the regex with additional phone number formats, I found that the current expression does not properly handle all optional characters and separators in the phone number format.

In addition, the test input contains a space after the closing parentheses ')', but the current regex only accounts for periods and hyphens as separators. This prevents the parenthesized format from being matched correctly.

Note: I have not modified the implementation yet. I will test additional phone number formats and variations of the regular expression to determine which cases are currently handled incorrectly. I will also refer to Python's regex documentation to better understand the behavior before proposing a specific change.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

agreement: 18/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in disclosure)
agreement: 19/20 scored items  (bar: 18/20: below the bar; category floor unmet: no match in disclosure)
agreement: 17/20 scored items  (bar: 18/20: below the bar)
agreement: 19/20 scored items  (bar: 18/20: PASS)

**Package analysis**

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

For pkg-10, my rubric initially decided reject, while the gold label was accept. The report could not reproduce the issue because its environment differed from the original, but it clearly documented the differences and explained why they might affect reproduction. I revised the Environment Check so that an environment mismatch does not automatically fail a cannot reproduce report.

After I revised the rubric for pkg-10, my pkg-11 check failed. The gold label was reject because the candidate claimed to reproduce the issue on a materially different environment from the original report. This helped me refine the rubric further: an environment mismatch can be acceptable for a clearly documented cannot reproduce attempt, but a claimed reproduction needs a comparable environment.

**Check rationale**

[Quote one check from the `rubric.md` you uploaded to `tools/repro-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

| Environment Checks | Check the original issue description for the stated environment, then check the claim comment/report for the environment used during reproduction. Look for the operating system, version used, and installation/setup steps.|Pass if the report clearly documents the testing environment and compares it with the original issue, without requiring the environments to match. For a claimed reproduction, the evidence must demonstrate the issue's actual behavior. For a cannot reproduce report, any relevant environment differences should be documented and considered as a possible explanation for the result. Fail if important environment information is missing, the environment is not meaningfully compared with the issue, or the evidence does not support the claimed result. | required |

Some of the reports could not reproduce the issue because its environment differed from the original, but it clearly documented the differences and explained why they might affect reproduction. I revised the Environment Check so that an environment mismatch does not automatically fail a cannot reproduce report. I had to revise again further since an environment mismatch can be acceptable for a clearly documented cannot reproduce attempt, but a claimed reproduction needs a comparable environment.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

For pkg-20, I made the disclosure check stricter so that a missing AI-use disclosure fails the check when the repository explicitly requires one. The trade-off is that the rubric may reject a comment that otherwise looks acceptable if it does not provide a required disclosure, but I accepted this because the repository's policy makes the disclosure a requirement.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
