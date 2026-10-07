# Procedure

## Read order

1. Read the plan draft and plan comment completely before grading.
2. Read the reproduction evidence to understand the reproduced failure and observed behavior.
3. Read the issue-thread highlights for maintainer requests, constraints, and prior decisions.
4. Read the repo-facts block for relevant files, structure, tests, and repository conventions.
5. Read each rubric check before assigning any grades.

## Evidence gathering

1. For diagnosis, locate the claimed root cause in the plan and compare it with the reproduced behavior and quoted repro evidence.
2. For scope, identify what the plan says will change, what will not change, and which files it proposes touching.
3. For executability, identify whether the files and approach give a developer enough information to begin the implementation without inventing missing decisions.
4. For the test plan, locate the reproduction steps the author plans to rerun and the expected observable result after the fix.
5. For uncertainty, identify claims presented as certain and compare them with the available evidence; note unresolved facts listed as risks or unknowns.
6. For thread and conventions, compare the plan comment with maintainer requests, issue-thread decisions, and repository conventions.

## Check execution

1. Grade each rubric check independently using only the evidence available in the package.
2. Mark a check as pass only when its pass condition is supported by specific evidence.
3. Mark a check as fail when the evidence contradicts the pass condition or clearly shows the requirement is not met.
4. Mark a check as unclear (`?`) when the package does not contain enough evidence to establish a pass.
5. Do not assume missing facts or give credit based on what the author might have intended.
6. Record the evidence and a short reason for every grade.

## Verdict assembly

1. Review the result of every required check.
2. Return `accept` only when every required check passes.
3. Return `reject` if any required check fails or is unclear.
4. Include concise feedback identifying the failed or unclear checks and what evidence is missing or contradictory.
5. End with the required JSON verdict using `accept` or `reject`.
