# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

keenan-qk

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73#issuecomment-6029122552

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73#issuecomment-6029230346

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

1. 17/20 — initial complete scored run. This was below the 18/20 agreement bar and also scored 0/1 in the disclosure category.

2. Targeted --only pkg-03,pkg-12,pkg-20 run after investigating the initial disagreements. pkg-03 and pkg-12 matched their gold labels, but pkg-20 still incorrectly accepted.

3. After adding an explicit AI-disclosure check, targeted runs fixed pkg-20, but pkg-12 exposed an ambiguity in how the rubric treated reproduction inputs referenced directly from an issue.

4. After clarifying the Steps evidence guidance, I ran the canary set --only pkg-03,pkg-12,pkg-20,pkg-18,pkg-04 three times. Each run matched all five gold labels: pkg-03 accept, pkg-12 accept, pkg-20 reject, pkg-18 reject, and pkg-04 reject.

5. Final complete run:
   `agreement: 19/20 scored items  (bar: 18/20: PASS)`

   `categories: clear-accept 7/8  disclosure 1/1  no-evidence 4/4  unfollowable-comms 3/3  wrong-target 4/4`


**Package analysis**

I focused on pkg-20. My initial rubric decided accept, while the gold label was reject. The package exposed a weakness in my original "Repo conventions followed" check: AI-use disclosure was hidden inside a broad repository-conventions criterion, so a package could satisfy the other repository conventions while still omitting disclosure required by repository policy.

I revised the rubric to make AI disclosure its own required check:

AI use disclosed | The claim comment and reproduction report, read against the repo-facts block and any repository AI-use or contribution policy | Pass if the repository has no applicable AI-disclosure requirement, or if required AI use is disclosed in the form the policy requires, including the tool and extent of assistance when required. Fail if the repository requires AI disclosure and the package omits it. | required

With that check explicit, pkg-20 changed to reject and matched its gold label.

**Check rationale**

The check I added to rubric.md is:

AI use disclosed | The claim comment and reproduction report, read against the repo-facts block and any repository AI-use or contribution policy | Pass if the repository has no applicable AI-disclosure requirement, or if required AI use is disclosed in the form the policy requires, including the tool and extent of assistance when required. Fail if the repository requires AI disclosure and the package omits it. | required

I made AI disclosure explicit because the earlier rubric folded it into the broader repository-conventions check. The initial full run showed that this was too permissive: pkg-20 was accepted even though its expected result was reject. Making disclosure a separate required check makes the decision depend directly on the repository's AI-use policy. It does not require disclosure where the repository has no applicable requirement, but it fails a package that omits disclosure when the repository requires it.

**Trade-offs**

Adding the explicit AI-disclosure check fixed pkg-20, but I did not want that change to make otherwise valid packages fail or hide problems in other categories. I therefore used a canary set of pkg-03, pkg-12, pkg-20, pkg-18, and pkg-04.

During those targeted runs, pkg-12 exposed a separate ambiguity: its reproduction referred unambiguously to inputs already stated in the issue instead of restating them. I clarified the Steps guidance to say that inputs, options, and commands stated exactly in the issue may be referenced when the reference is unambiguous. I kept pkg-18 in the canary set to make sure this clarification did not make genuinely unfollowable reproduction steps pass.

I ran the five-package canary set three times after the changes. All five matched their gold labels on all three runs. The final complete run then scored 19/20 and passed every category floor. I accepted the remaining miss rather than loosening the rubric further just to reach 20/20.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/repro-check/`.
