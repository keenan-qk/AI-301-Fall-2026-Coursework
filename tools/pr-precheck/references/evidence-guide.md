# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

**Where it lives:** In an eval package, compare the plan-context block's scope, implementation approach, and deviation notes with the candidate PR's unified diff and changed files. Also compare claims in the PR title and description with what the diff actually implements. In live mode, read `plan.md`, including its deviation notes, and compare it with the complete branch diff from `git diff main...HEAD` and the draft PR title and description.

**What good looks like:** Every behavior-changing part of the diff falls within the accepted plan or is accounted for by a recorded deviation. Work from the original plan that is absent or changed is honestly recorded when relevant, and the PR description accurately represents what the diff delivers. Undisclosed extra work, missing planned work with no deviation note, or description claims contradicted by the diff are silent drift.

## Test evidence (harness category: not-tested)

**Where it lives:** In an eval package, compare the candidate PR's test-evidence section with the plan-context test plan and reproduction evidence, then read the repo-facts block for the repository's own applicable checks or test commands. In live mode, compare the captured before/after or reproduction evidence with the test plan in `plan.md` and inspect the recorded outcome of the repository's applicable checks or test suite.

**What good looks like:** The evidence names the behavior exercised and shows an observable result that distinguishes the implemented behavior from the reproduced failure. Applicable repository checks or tests have an outcome visible in the evidence. A bare statement such as "tests pass," without observable supporting evidence, is not sufficient.

## Diff quality (harness category: unreviewable)

**Where it lives:** In an eval package, inspect the candidate PR's unified diff and commit list, comparing the changed files and hunks with the work justified by the plan and recorded deviations. In live mode, inspect the complete branch diff from `git diff main...HEAD` and the branch's commits.

**What good looks like:** The intended fix can be reviewed without unrelated work obscuring it. Changed files and hunks are necessary for the planned change or a recorded deviation and do not contain leftover debug output, dead or commented-out code, unrelated refactors, formatting churn, generated noise, or drive-by edits.

## Standards and comms (harness category: standards-wall)

**Where it lives:** In an eval package, read the repo-facts block for PR-template requirements, contribution instructions, stated policies, AI-use disclosure requirements, and explicit maintainer direction in the issue context. Compare those requirements with the candidate PR's title and description. In live mode, read the repository's PR template, relevant contribution documentation and stated policies, and relevant maintainer instructions on the issue, then compare them with the draft PR title and description.

**What good looks like:** Every applicable repository or maintainer requirement is satisfied with substantive and truthful content. Required template sections are completed, required disclosures are present, and relevant explicit maintainer or contribution instructions are followed. Description claims also remain consistent with the actual diff; contradictions between the description and implementation are treated as plan-fidelity failures rather than merely communication problems.
