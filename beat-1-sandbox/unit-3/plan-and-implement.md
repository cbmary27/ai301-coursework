# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

cbmary27

**Plan comment**

Plan
Diagnosis
Problem
PIIScrubber does not detect or redact US phone numbers in the parenthesized format (555) 123-4567, even though it detects and redacts the equivalent hyphenated format 555-123-4567.

Reproduction Evidence
The Unit 2 reproduction demonstrated the problem using PIIScrubber directly:

print(s.scrub('Call me at (555) 123-4567 or 555-123-4567'))

The observed output was:

Call me at (555) 123-4567 or [REDACTED]

The reproduction also showed that:

print(s.detect('Call me at (555) 123-4567'))

returned:

[]

The additional issue tests produced:

21 deselected, 4 xfailed in 1.27s

This demonstrates that (555) 123-4567 is not currently handled by the phone-number detection/redaction logic, while 555-123-4567 is redacted.

The current phone_us regular expression allows an optional ) after the three-digit area code and allows an optional hyphen or period as the separator before the next three digits. It does not allow whitespace at that position. Therefore, the space in (555) 123-4567 prevents the full phone number from matching.

Scope
What I Will Change
safety/pii_scrubber.py - update the phone_us regular expression so that the supported parenthesized US phone format (555) 123-4567 can be detected.
tests/unit/test_pii_scrubber.py - add or update tests to verify detection and redaction of (555) 123-4567.
Verify that existing supported formats, including 555-123-4567, continue to work.
What I Will Not Change
I will not modify unrelated PII patterns such as email, SSN, international phone numbers, or street addresses.
I will not change the overall scrub() or detect() implementation unless testing shows that it is necessary for the phone-number fix.
I will not modify repository setup or application configuration.
I will not include the temporary claim_draft/test_PII.py reproduction script as part of the implementation.
Files
Files I expect to touch:

safety/pii_scrubber.py - update the phone_us regular expression.
tests/unit/test_pii_scrubber.py - add or update tests for the affected phone-number format.

The temporary claim_draft/test_PII.py file was created only for the Unit 2 reproduction and is not part of the intended implementation.

Approach
Update the phone_us regular expression in safety/pii_scrubber.py to support the phone formats identified in the reproduction.

Update the separator character classes so that a space is accepted in addition to the existing hyphen and period separators. This allows formats such as:555-123-4567
555 123 4567
555.123.4567
(555) 123-4567

Update the country-code portion of the expression so that +1 is matched together rather than allowing the regex to begin at the 1 and leave the + behind. The country-code portion should continue to support the existing 1 format.

Update the phone-number boundary handling so that parenthesized numbers such as (555) 123-4567 can be matched as a complete phone number rather than starting the match at 555 and leaving the opening parenthesis behind.

Keep the change limited to the phone_us pattern. The scrub() and detect() implementations will not be changed because the reproduction shows that the problem is in the phone-number matching pattern.

Add or update unit tests in tests/unit/test_pii_scrubber.py for the affected formats, including (555) 123-4567 and +1-555-123-4567, while retaining coverage for the existing 555-123-4567 format.

Run the relevant phone-number tests. The fix will be considered successful when the affected phone numbers are detected and completely replaced by [REDACTED], including the + and parentheses where present.

Test Plan
Reproduction Steps
I will re-run the Unit 2 reproduction:

Activate the Python virtual environment.
Run: PYTHONPATH=. python claim_draft/test_PII.py
Verify the output of scrub() for: Call me at (555) 123-4567 or 555-123-4567
Verify the result of detect() for: (555) 123-4567
Expected Result After the Fix
For:

Call me at (555) 123-4567 or 555-123-4567

both phone numbers should be redacted.

The result should therefore contain:

Call me at [REDACTED] or [REDACTED]

The corresponding detect() call should return a phone PII detection for (555) 123-4567 instead of an empty list.

Pass Condition
The fix passes if:

(555) 123-4567 is detected as phone_us PII.
scrub() replaces (555) 123-4567 with [REDACTED].
555-123-4567 continues to be detected and redacted.
The relevant phone-number tests pass.
The reproduction no longer produces the previously observed unredacted (555) 123-4567 result.

Risks and Unknowns
Changing the phone_us regular expression could unintentionally affect other supported phone-number formats. Different combinations of country codes, parentheses, spaces, hyphens, and periods should be tested to make sure the updated pattern does not introduce regressions. The pattern should be tested against both the newly supported (555) 123-4567 format and the existing formats to confirm that the complete phone number is detected and redacted.

---

## Your branch

**Branch**

[The name of the branch you built the change on, exactly as it appears in your fork. The
naming shape is a type prefix, then the issue number, then a short description. **The issue
number in the branch name must be the number of the issue you claimed** — a name carrying
any other number does not satisfy this field.]

fix/53-pii-phone-redaction

**Evidence**

[Your Unit 2 reproduction steps re-run against the built change: the before, then the
after. Paste both, including the commands you ran and their output.]

Before (from unit 2 reproduction report):

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

After:

Running the test code:

$ PYTHONPATH=. python claim_draft/test_PII.py                                                       Call me at [REDACTED] or [REDACTED]
2026-10-06 13:16:05 [info     ] pii_detected                   count=1 types=1
[{'type': 'phone_us', 'value': '(555) 123-4567', 'start': 11, 'end': 25}]
(.venv)

$ pytest -q tests/unit/test_pii_scrubber.py -k "test_us_phone_number_redaction or test_us_phone_formats or test_detect_phone_pii or test_phone_at_start_of_text"
XXXX                                                                                         [100%]
21 deselected, 4 xpassed in 0.50s
(.venv)

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]

agreement: 19/20 scored items  (bar: 18/20: PASS)

**Package analysis**

[Pick one scored package (`pkg-01` through `pkg-20` — the four `calib-` packages are never
scored). Name it by id, say what your rubric decided and what the gold label said, and
explain why your rubric read it that way.]

Package 20 - My rubric labelled this package as accept while the gold label was reject. The error boils down to the thread-convention. My rubric failed for this package mainly because my rubric does not have requirements to check for disclosure statements in the plan and to compare them with the repo's required contribution policy and disclosure usage.

**Check rationale**

[Quote one check from the `rubric.md` you uploaded to `tools/plan-check/`, exactly as it reads now.
Then say why it reads that way — what you revised to get there, or what you rejected in
favour of it.]

| Scope  | The plan's scope and the files/code locations it identifies for the change. | Pass if the scope identifies where the bug occurs (such as a file, function, class, or relevant code location) and clearly states what will and will not be changed.  | Required |

The check reads this way because I wanted the plan to clearly identify the specific code locations that would be involved in the proposed fix. During the revision of the rubric, I focused on requiring the user to identify where the bug occurs and what files, functions, classes, or other relevant locations would be changed. I also included what will and will not be changed so that the scope of the proposed solution is clearly defined and does not expand beyond the issue.

**Trade-offs**

[Every check gives something up. Any one of these is a complete answer: a package whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

The trade-off in my rubric is that requiring all checks to pass makes the evaluation stricter. A plan may have a reasonable approach but still be rejected if it is missing important evidence for one of the required areas. I accepted this trade-off because the goal is to ensure that an accepted plan has a clear diagnosis, well-defined scope, and reproducible test plan rather than only a generally reasonable solution.
---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
