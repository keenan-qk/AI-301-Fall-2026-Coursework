# Procedure: how this tool grades a PR package

## Read order

1. Read the accepted plan first, including its scope, implementation approach, test plan, and recorded deviation notes. Record what work the PR is expected to contain and what testing is expected to demonstrate.
2. Read the issue context and repo facts for requirements that constrain the implementation or submission, including maintainer directions, PR-template asks, contribution policy, and disclosure requirements.
3. Read the candidate PR's unified diff and commit list. Record the changed files, the behavior-changing hunks, and any changes that do not appear to follow from the plan or a recorded deviation.
4. Read the candidate PR's title and description after inspecting the diff. Record the implementation, completeness, testing, and limitation claims the PR makes so those claims can be checked against what the diff actually delivers.
5. Read the candidate PR's test evidence. Record the reproduction path exercised, the observable before/after or expected-after result, and the outcome of applicable repository checks.
6. Read the rubric checks in order before assigning grades. Use the gathered evidence for the side-by-side comparisons rather than grading from the PR's presentation alone.

## Evidence gathering

1. For plan fidelity, compare every behavior-changing file and hunk in the diff with the plan's stated scope and implementation approach. If they differ, check the plan's deviation notes before treating the mismatch as silent drift. Also identify planned work that is absent from the diff and determine whether that difference is recorded.
2. For description fidelity, list the material claims made by the PR title and description and compare each with the unified diff, test evidence, and recorded deviations. Record any claim of behavior, completeness, or testing that those sources do not support.
3. For test evidence, compare the evidence with the plan's test plan and reproduction evidence. Identify the behavior exercised, the observable expected result, the observed result, and the visible outcome of applicable repository checks or test suite.
4. For diff quality, inspect the diff and commit list for changes unrelated to the planned implementation or recorded deviations. Record debug artifacts, dead or commented-out code, formatting churn, generated noise, unrelated refactors, or drive-by edits when present.
5. For standards, identify every applicable PR-template ask, contribution rule, disclosure requirement, and explicit maintainer instruction from the repo facts and issue context. Compare each requirement with the candidate PR title and description and record whether it is substantively satisfied.

## Check execution

1. Execute the rubric checks in their listed order using the evidence gathered above.
2. Grade a check `pass` only when specific package evidence establishes its pass condition.
3. Grade a check `fail` when package evidence contradicts the pass condition or affirmatively shows that the condition is not met.
4. Grade a check `unclear` when the evidence needed to establish the required condition is genuinely absent or insufficient.
5. Do not infer missing implementation, testing, disclosures, deviations, or repository compliance from intent or from statements that are not supported elsewhere in the package.
6. A disclosed limitation, deferred item, or implementation change does not fail a check merely because the completed work differs from the original plan. Apply the rubric to whether the difference is recorded honestly, the resulting diff remains reviewable, and the description accurately states what was delivered.
7. Record one concise evidence line for every check, naming the fact or quote that determined the grade. Do not re-read the whole package when the gathered evidence already resolves the check; return to the source only when the recorded evidence is insufficient to apply the pass condition.

## Verdict assembly

1. Review every required check grade after all checks have executed.
2. Apply the rubric's verdict rule exactly: return `accept` only if every required check passes; return `reject` if any required check fails or is unclear.
3. If the verdict is `reject`, identify the first failing or unclear required check in rubric order as the primary deciding check. If multiple required checks fail, report the others as additional failures without changing which check is primary.
4. In the readable summary, give concise feedback for failed or unclear checks and identify the evidence that caused the result. Do not add requirements that do not exist in the rubric.
5. Emit every check and its evidence in the required JSON output, followed by the binary `accept` or `reject` verdict. The fenced JSON block must be valid and must be the final content in the response.
