# Rubric: is this plan ready to post and build from?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here (via your procedure.md). It ships empty on
purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the plan's scope statement, the test plan read against
     the repro evidence's steps, the plan comment read against the
     thread highlights, the repo-facts block) or a location from your
     references/evidence-guide.md. "The plan" is not a source; "the
     plan's stated cause read against what the repro evidence shows"
     is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (is
     this one bounded change? could a stranger start executing it?),
     never the write-up's shape (how many sections it has, how long it
     is, whether it uses headings). Structure-shaped checks are what
     make graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad plans posted. The lecture named the
failure families: the diagnosis ignores or contradicts the reproduced
evidence, the change is unbounded (scope creep), the plan targets the
symptom while the evidence points at the cause, a stranger could not
start executing it, the test plan proves nothing observable, the
unknowns are dressed up as certainty, and the comment ignores what the
thread or the repo's stated conventions ask. A rubric that ignores a
family will fail eval packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| diagnosis | The plan's stated cause read against the repro evidence's steps, observed behavior, and quoted evidence | The stated cause is supported by and does not contradict the reproduced behavior, and the proposed fix addresses that cause rather than only the visible symptom. | required |
| scope | The plan's scope statement, files to touch, approach, and repo-facts block | The proposed work is one bounded change needed to fix the reproduced issue; unrelated refactors, migrations, documentation work, or other while-here changes are excluded. | required |
| executable | The plan's files-to-touch and approach read against the repo-facts block | A developer unfamiliar with the issue could identify where to start and what change to make without having to invent a missing implementation decision. Pass if the plan names the file or subsystem and the change to make. Exact functions may be left to locate as long as the plan states how they will be located, such as through a trace, log, or named entry point. | required |
| test-plan | The plan's test plan read against the repro evidence's original steps and observed behavior | The test plan reruns the relevant reproduction path and states a concrete, observable expected result that distinguishes the fixed behavior from the reproduced failure. | required |
| uncertainty | The plan's diagnosis, risks, unknowns, and approach read against the available repro evidence and repo facts | Claims that the diagnosis or fix direction depends on are supported by the available evidence. Unresolved facts that would change the diagnosis or fix direction are identified as risks or unknowns. Implementation details a developer would confirm by reading the named file, such as where a timestamp is stored, do not fail this check. | required |
| thread-conventions | The plan comment read against the issue-thread highlights and the repo-facts block, including stated maintainer requests and repository conventions | The comment respects relevant maintainer constraints and repository conventions, does not promise work outside the plan, and does not contradict material information already established in the thread. | required |

## Verdict rule

Accept only if every required check passes. Reject if any required
check fails or is unclear. Preferred checks, if any are added later,
may provide feedback but never change the verdict.
