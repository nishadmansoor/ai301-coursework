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
