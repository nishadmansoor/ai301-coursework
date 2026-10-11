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

## Who I am in threads

<!-- 2-3 lines. Who is talking when you comment on an issue: your
experience level stated plainly, what you are doing in this repo, what
readers can expect from you. This is the register your rules protect. -->
I am a student contributor reproducing an issue as part of the Path Review workflow. I describe what I have tested myself and observed rather than presenting someone else’s reproduction as my own.

I think the readers should be able to tell the difference between the issue’s existing information, what I tested, and what I concluded from my evidence.

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
Rule: Being very specific about what I tested

Instead of being vague about what I did, I will properly describe the specific command, version, or action that I tested.
  -Wrong: "I tested this and can confirm that there is an issue here"
  -Right: "I tested this using [command] on [version #], and confirm I ran into the same issue that was previously described"

Rule: Separating observation from opinion

I will report only what I actually observed during testing, instead of presenting my assumptions about what caused the issue as a fact.
  -Wrong: "The dependency is causing this error"
  -Right: "I observed the error after installing the dependency, but I did not confirm/verify that the dependency is the cause of the error"

Rule: Give enough context to reproduce my results
I will include the relevant steps and setups so another person repeat what I did & understand how I got my results.
  -Wrong: "I got the same error"
  -Right: "I installed [version#] on [device specifics], ran the command from the issue, and received the following error [error]"
  
## Things I never post
<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->
-Vague statements
-Conclusions that don't match my evidence
-Unnecessary background information that does not help solve/attempt to solve the issue
-Claims about tests I didn't personally run
-Speculative/opinionated statements

## PR-specific writing rules

### Rule: Make the title describe the actual change

The PR title should use the repository's Conventional Commit format and describe the code change directly.

- Wrong: "Fix JSON array output parsing for Issue #69"
- Right: "fix(rag): handle top-level JSON arrays in output parser"

### Rule: Keep the description aligned with the diff

Every change listed in the PR description must correspond to something actually changed. Test results belong in the Testing section, not in the Changes list.

- Wrong: "Changes: fixed the parser, verified everything, and improved quality."
- Right: "Changes: handle top-level JSON arrays in the output parser and update the regression test."

### Rule: Report test results honestly

I will distinguish passing checks from checks that failed, could not run, or collected no tests. I will not claim that CI is green before the CI results confirm it.

- Wrong: "All tests pass."
- Right: "The unit suite passed; integration tests could not be verified because pytest collected no tests and exited with error 5."

### Rule: Disclose AI assistance and limitations plainly

I will include the required AI-use disclosure and explain meaningful limitations without exaggerating their impact or hiding them.

- Wrong: "Everything was fully verified."
- Right: "AI assisted with planning and validation. Integration-test coverage remains unverified because no integration tests were collected."

## Things I never post: PR-specific additions

- A PR title that ignores the repository's required naming convention.
- A claim that a check passed when its result does not support that claim.
- A change description that promises more than the diff implements.
- A claim that CI is green before checking the actual CI results.
