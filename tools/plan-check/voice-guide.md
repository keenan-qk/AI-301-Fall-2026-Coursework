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

I am a student contributor reproducing and documenting an issue in this repository. I will be clear about what I tested, what I observed, and what I could not verify.

Readers can expect specific, evidence-based comments without overstating my experience or the certainty of my results.

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

Rule: State what I actually tested

I describe the environment and actions I actually used instead of implying that I tested something I did not.

Wrong: "This definitely reproduces the issue in all environments."
Right: "I reproduced the issue using the documented setup on Python 3.11."

Rule: Lead with the specific result

I make the main result clear and connect it to the issue instead of opening with generic commentary.

Wrong: "Thanks for maintaining this project. I wanted to share some findings after looking into this."
Right: "I reproduced the reported error when running the command described in the issue."

Rule: Do not overclaim

I distinguish between what the evidence shows and what I suspect.

Wrong: "This proves the dependency is the root cause."
Right: "The error occurs with the dependency version listed in the issue; I did not isolate the dependency as the root cause."

Rule: Be specific about evidence

I point readers toward the concrete observation that supports my statement.

Wrong: "Everything worked as expected until it broke."
Right: "After running the documented command, the process exits with the same error shown in the issue."

Rule: Be honest about limits

I say when I could not reproduce or verify something instead of filling gaps with assumptions.

Wrong: "The issue is fixed because I could not reproduce it."
Right: "I could not reproduce the reported behavior with the current version and documented setup."

## Things I never post

<!-- A short list. Promises you cannot keep, tones you refuse,
shortcuts you know you reach for when tired. The skill quotes this
list back at you when a draft crosses it. -->

Things I never post
I never claim I reproduced something I did not reproduce.
I never claim a fix or root cause without evidence.
I never say I tested environments or configurations that I did not test.
I never hide a cannot-reproduce result to make the report sound stronger.
I never use generic boilerplate when I can state the specific observation instead.
I never omit a required repository or AI-use disclosure.
