# Evidence guide: where proof lives in a reproduction package

<!--
THIS IS THE PART YOU WRITE (new this week: Unit 1 handed you this file
finished; the scaffolding fades). The skill uses this guide as its map:
for every kind of proof a rubric check names, this file says WHERE to
find it in a package and WHAT GOOD LOOKS LIKE when you do.

Under each family heading below, write:

- Where it lives: the exact places to look. In an eval bundle (which
  section of the package: the issue context, the repo-facts block, the
  claim comment, the repro report and its parts). In live mode (where
  on GitHub or in the draft: the issue thread, the repo's docs, the
  student's draft comment).
- What good looks like: one or two sentences someone else could apply.
  Prefer observable conditions ("the versions named match what the
  issue targets, or the difference is called out") over adjectives
  ("environment is thorough").

A rubric check whose evidence this guide cannot locate is a check
nobody else can execute; the rubric swap showed you what that feels
like. Write the map you wish your grader had.
-->

## Environment

<!-- Where the environment record lives, and what a sufficient one
looks like against the issue's stated target. -->

Where it lives: The repro report's environment record in the evaluation package; in live mode, use the environment information recorded in the student's reproduction report and compare it with the issue's stated versions and setup requirements.

What good looks like: The record identifies the relevant OS/runtime, package or dependency versions, and other setup details needed to understand or reproduce the behavior. If the environment differs from the issue's target, the difference is explicitly called out.

## Steps

<!-- Where the reproduction steps live, and what makes them followable
by a stranger, starting state to trigger. -->

Where it lives: The reproduction steps in the repro report, beginning with the stated starting state and ending at the action that triggers the issue.

What good looks like: The steps contain enough concrete actions for a stranger to start from the recorded state and reach the reported behavior without guessing about omitted setup or actions. Inputs, options, and commands already stated exactly in the issue may be referenced rather than restated, as long as the reference is unambiguous (for example, "the issue's two inputs with its stated ranges"); count them as part of the steps and as satisfying a template's input or reproduction field.

## Behavior shown

<!-- Where the artifacts live (output excerpts, logs, screenshots),
and what it means for an artifact to show the issue's behavior rather
than an adjacent one. -->

Where it lives: The output excerpts, logs, screenshots, command results, or other reproduction artifacts in the repro report; compare these directly with the behavior or error described in the issue.

What good looks like: The artifacts show the issue's actual behavior or error, including enough surrounding evidence to distinguish it from a similar or adjacent problem. The evidence should support the specific behavior claimed in the report.

## Honesty

<!-- Where claims and their backing meet: how to tell a report that
says exactly what happened (including an honest cannot-reproduce) from
one that claims more than its evidence shows. -->

Where it lives: The outcome statement in the reproduction report and the evidence immediately supporting that statement; for claims, compare the claim comment with the issue evidence it references.

What good looks like: The stated outcome matches what the evidence demonstrates. A cannot-reproduce result is stated as cannot-reproduce when that is what happened, rather than being turned into a stronger claim. A reproduced result is supported by artifacts showing the issue's behavior.


## Comms

<!-- Where the words meet the repo: the claim comment against the
issue, the comments against the repo's stated templates and
contribution policy (including AI-use disclosure requirements), and
what specific-and-honest looks like next to boilerplate. -->

Where it lives: The claim comment and reproduction comment, evaluated against the issue thread, repo-facts block, repository contribution guidance, comment templates, and any AI-use disclosure requirements.

What good looks like: Comments identify the specific issue and make claims that are supported by the available evidence. Required repository conventions and disclosures are followed, and generic boilerplate is not used in place of issue-specific information.
