# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| plan-fidelity | The candidate PR's unified diff and changed files read against the plan-context block's stated scope, implementation approach, and recorded deviation notes | Every behavior-changing part of the diff is within the accepted plan or is accounted for by a recorded deviation. Planned work that is absent from the diff does not fail this check when the omission or change is explicitly recorded as a deviation; an unrecorded mismatch in either direction fails. | required |
| description-fidelity | The candidate PR's title and description read against the unified diff, plan context, and recorded deviations | The title and description accurately describe what the diff actually delivers and do not claim implementation, behavior, testing, or completeness that the package does not demonstrate. Disclosed limitations or deferred work pass when they accurately reflect the diff and recorded deviations. | required |
| test-evidence | The candidate PR's test-evidence section read against the plan-context test plan, reproduction evidence, and the repository's stated checks | The evidence shows an observable outcome for the relevant reproduction path that distinguishes the implemented behavior from the reproduced failure, and shows the outcome of applicable repository checks or test suite. A bare claim such as "tests pass" without an observable result does not pass. | required |
| diff-quality | The candidate PR's unified diff and commit list read against the change required by the plan | The intended change is reviewable in the diff without unrelated work or leftover debris. Debug artifacts, dead or commented-out code, unrelated refactors, formatting churn, generated noise, or drive-by edits fail when they are not necessary to the planned change or a recorded deviation. | required |
| standards | The candidate PR's title and description read against the repo-facts block's PR-template asks, contribution instructions, stated policies, AI-use disclosure requirements, and explicit maintainer direction in the issue context | The PR satisfies each applicable repository or maintainer requirement: required template asks contain substantive answers, required disclosures are present and truthful, and explicit contribution or maintainer instructions relevant to the submission are followed. A requirement that the package shows is not applicable does not cause failure. | required |

## Verdict rule

Accept only if every required check passes. Reject if any required check fails or is unclear. An `unclear` grade counts as a failure because a required condition that cannot be verified from the available package evidence is not ready to submit. Preferred checks, if any are added later, may provide feedback but never change the verdict.
