# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

**Where it lives:** In an eval package, read the candidate plan's diagnosis together with the repro-evidence block, especially the reproduction steps, observed behavior, and quoted evidence. In live mode, compare the diagnosis in `plan.md` with the student's posted repro comment and the relevant issue-thread evidence.

**What good looks like:** The stated cause explains behavior that the repro evidence actually demonstrates and does not contradict that evidence. The proposed change addresses the identified cause rather than only the visible symptom.

## Scope

**Where it lives:** In an eval package, read the candidate plan's in-scope and not-in-scope statements, files or areas to touch, and the repo-facts block. In live mode, use the scope, files, and approach in `plan.md` together with the repository structure and issue requirements.

**What good looks like:** The work is bounded to the reproduced issue and identifies both what will change and what will remain unchanged. Files and tasks are necessary for that change rather than unrelated refactors, migrations, documentation work, or other drive-by improvements.

## Executability

**Where it lives:** In an eval package, read the candidate plan's files or areas to touch and its implementation approach, then compare those claims with the repo-facts block. In live mode, use the files and approach in `plan.md` and verify relevant repository locations when needed.

**What good looks like:** The plan identifies where implementation starts and what change will be made clearly enough that another developer could begin the work without inventing a missing implementation decision.

## Test plan

**Where it lives:** In an eval package, read the candidate plan's test plan together with the repro-evidence block's commands, steps, observed output, and artifacts. In live mode, compare the test plan in `plan.md` with the student's posted reproduction steps and evidence.

**What good looks like:** The test plan reruns the relevant reproduction path and states a concrete observable result expected after the fix. The expected result distinguishes the fixed behavior from the original reproduced failure rather than merely saying to run tests or confirm that it works.

## Honesty

**Where it lives:** In an eval package, read the candidate plan's diagnosis, risks, unknowns, and deviations and compare factual claims with the repro evidence and repo-facts block. In live mode, read the same sections of `plan.md`; after implementation, also inspect the `## Deviations` section.

**What good looks like:** Claims presented as certain are supported by available evidence. Facts that have not been established and could affect implementation are identified as risks or unknowns instead of being presented as certain, and changes from the accepted plan are recorded honestly under Deviations.

## Comms

**Where it lives:** In an eval package, read the plan comment against the issue context or thread highlights and the repo-facts block, including contribution instructions, templates, maintainer requests, and any AI-use disclosure requirements. In live mode, compare `comment.md` with the GitHub issue thread and the repository's contribution documentation.

**What good looks like:** The comment responds to relevant maintainer requests and established thread decisions, follows applicable repository contribution conventions, and promises only work supported by the plan. It communicates the diagnosis, intended change, and proof of success without ignoring or contradicting material context from the thread.
