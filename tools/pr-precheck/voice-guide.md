# Voice guide: how I talk upstream

<!--
THIS IS A CARRY-OVER SLOT, not a new hole. You wrote this guide in
week 2 and carried it through week 3; paste your filled voice-guide.md
here, whole. It is not re-authored and it is not graded as new work
this week.

Then reread it with the PR in mind. Your comments promised, reported,
and committed to an approach; a PR title and description ask a
maintainer to spend review time on your work. If your rules do not
cover that register (for example: how a title earns its thirty
seconds, how a description promises exactly what the diff contains,
how a disclosed shortfall is worded so it reads as honesty rather
than apology), extend the guide with what it needs. Extending is
allowed and encouraged; starting over is not required.

Live mode reads this file and holds your draft PR title and
description against it, reporting any rule your draft breaks. Eval
mode ignores it entirely, because your voice is yours and carries no
gold labels.
-->


## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->

I’m a graduate student, contributing to open-source for the first time in this repository and learning the project through issue reproduction. My comments should make it clear what I personally observed and what I plan to investigate, without pretending to know more than I do.

## Rules I write by

<!-- 3-5 rules, drafted from the lecture's slide-12 moment. Each rule
needs a wrong/right pair from your own hand: one line you might
actually have written that breaks the rule, and the line you would
post instead. The pair is what makes a rule executable; a rule without
one is a wish.

Format each rule like this:

### Rule: <short name>

<The rule, one or two sentences.>

- Wrong: "<a line that breaks it>"
- Right: "<the line to post instead>"
-->

Rule: Name the specific issue

- Wrong: "I would like to work on this issue"
- Right: "I would like to work on the issue described in #53. I will test to reproduce the behaviour and will reply to this comment as soon as it is done"

Rule: Don't claim reproduction before testing

- Wrong: "I have reproduced the behaviour in the issue with the stated environment"
- Right: "I have reproduced the 'Null Pointer Issue' as described in issue #53 with the following environment: MacOS 15.0, Python version 3.13"

Rule: Don't promise a fix

- Wrong: "I have a solution in mind to solve the issue"
- Right: "I have a potential approach I can investigate after reproducing the issue: modifying the existing validation logic to handle the missing value"

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

- I will never claim that I have reproduced an issue before I actually have tested it.
- I never report a concrete fix when my claim is only about reproduction.
- I will not merely assert that the required behaviour has been observed without listing out the steps that I followed to reproduce the issue.
- I will never state that something works or fails without saying what I actually observed.

# Voice guide: how I talk upstream

<!--
THIS IS THE PART YOU WRITE (new this week). Live mode reads this file
before any comment of yours goes out the door; eval mode ignores it
entirely, because your voice is yours and carries no gold labels.

This is not etiquette. "Be polite and concise" is advice for everyone
and therefore rules for no one. Write rules YOU need, in your own
words, each one concrete enough that the skill can hold a draft
against it and say which rule it breaks.

Three sections. Fill all three.
-->

## How I describe my experience

I describe what I personally did and observed rather than presenting assumptions as facts. When I have not verified something, I describe it as something I plan to investigate rather than something I already know.

* **Wrong:** "I understand the cause of this issue and know how to fix it."
* **Right:** "I have reproduced the issue and will investigate the cause before proposing a fix."

## How I describe technical findings

I use specific evidence when describing an issue, such as the command I ran, the behavior I observed, or the file and function involved. I avoid vague statements that do not tell the reader what I actually found.

* **Wrong:** "The validation is broken and needs to be fixed."
* **Right:** "The validation returns an error when the input is missing. I observed this when running the reproduction steps described in #53."

## How I describe plans and next steps

I distinguish between what I have already verified and what I intend to do next. I can suggest a potential approach, but I do not present an untested approach as a confirmed solution.

* **Wrong:** "I will fix the validation logic so the error no longer occurs."
* **Right:** "After confirming the cause, I plan to investigate whether the validation logic should handle the missing value explicitly."
