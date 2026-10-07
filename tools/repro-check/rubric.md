# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded| The repro report's environment record, including versions, OS/runtime, dependencies, and any issue-specific setup needed to trigger the behavior | Pass if the recorded environment identifies the relevant versions and setup needed to reproduce the issue, or explicitly identifies a meaningful difference from the issue's stated target | required  |
| Steps followable  | The repro report's reproduction steps, read from the stated starting state through the trigger action  | Pass if a stranger could follow the steps from the recorded starting state and reach the reported behavior without needing missing actions or unstated setup  | required  |
| Behavior matches issue  | The output excerpts, logs, screenshots, or other artifacts produced during reproduction, read against the issue description and error/behavior it reports  | Pass if the artifacts demonstrate the same behavior or error described by the issue, rather than a related or adjacent failure  | required |
| Outcome is honest  | The repro report's outcome statement together with the artifacts and evidence supporting it  | Pass if the stated outcome matches the evidence. A clearly evidenced cannot-reproduce outcome passes; a claim of reproduction passes only when the evidence shows the issue behavior  | required  |
| Repo conventions followed  | The claim comment and reproduction comment, read against the issue thread, repo-facts block, repository contribution guidance, templates, and AI-use disclosure requirements  | Pass if the comments follow applicable repository conventions and disclosures, and make only claims supported by the evidence  | required  |
| AI use disclosed | The claim comment and reproduction report, read against the repo-facts block and any repository AI-use or contribution policy | Pass if the repository has no applicable AI-disclosure requirement, or if required AI use is disclosed in the form the policy requires, including the tool and extent of assistance when required. Fail if the repository requires AI disclosure and the package omits it. | required |

## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict;
unclear counts as fail." -->

Accept if every required check passes. Any required check that fails makes the package reject. An unclear required check counts as a fail. There are no preferred checks in this rubric, so every listed check affects readiness.
