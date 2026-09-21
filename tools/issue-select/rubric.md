# Rubric: is this a good first issue?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever checks
you define here. It ships empty on purpose: the judgment is your work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where. Name the source
     (repo-facts block, issue body, comment thread, or the locations in
     references/evidence-guide.md). "The repo" is not a source; "the last
     5 default-branch commit dates" is.
   - Pass condition: a condition someone else could apply and get your
     answer. Prefer thresholds with numbers ("a maintainer commented
     within 30 days") over adjectives ("maintainer is responsive").
   - Weight: `required` (a fail here rejects the issue) or `preferred`
     (never changes the verdict; a nice-to-have that helps rank the
     issues you accept).

2. A verdict rule below the table: how the check grades combine into
   accept or reject, including how `unclear` is treated. The verdict
   space is binary. If you write no rule for `unclear`, the skill treats
   it as fail.

Cover what actually kills first contributions. The lecture named four
families: the maintainer is alive, the repo is in use, the scope fits a
newcomer, and nobody else is already on it. A rubric that ignores a family
will fail eval issues designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| maintainer_activity | The issue comment thread, PR activity, and the last 90 days of repository activity in `repo-facts` | At least one maintainer or repository contributor has demonstrated activity within the last 90 days through a comment, issue/PR action, merged PR, commit, or release. | required |
| repo_activity | The last 5 default-branch commit dates and repository activity in `repo-facts` | The repository has at least one meaningful activity signal within the last 90 days. | required |
| unassigned | Issue body, issue metadata, and comment thread | No contributor is assigned to the issue, and there is no evidence that someone is actively working on it, such as an explicit claim, active PR, draft PR, or linked branch/work. | required |
| newcomer_scope | Issue body, labels, comment thread, and the `this issue: assignees / linked PRs` line in the repo-facts block | The issue is **one unit of work whose finished state the issue itself already fixes**. Fail if any of: **(a) Umbrella or stream** — the body references 2 or more separate issue numbers as the work items, or invites ongoing/repeated contribution over time ("incrementally", "PRs welcome big and small", "megaissue"), or repo-facts shows 3 or more linked PRs already merged against it, or the thread shows contributors each claiming a different sub-target. An enumerated list of files, pages, or same-kind items that a single PR would land together does **not** fire this clause, however long, and a trailing "etc." in such a list does not make it open-ended. **(b) Unsettled core** — the issue's *primary* deliverable is still proposed rather than decided, and no maintainer comment settles it: hedging on the core ask ("perhaps we could", "likely surface", "TBD", "out of scope for v1"), a target behavior taken from an unverified or contradicted external spec, or a required asset/product decision the issue says does not exist yet. A hedge confined to an item the issue itself marks optional or lower-priority does not fire this clause. **(c) Abandoned-attempt history** — 2 or more linked PRs are closed unmerged, or the thread shows 3 or more prior claimants who did not finish. **(d) New feature surface** — the issue asks for a new user-facing tool, element, command, or endpoint **in the application** (documentation is excluded), wired across more than one subsystem. Restoring, completing, or extending coverage of a capability the product already has does **not** fire this clause. Otherwise pass. Do not fail for number of files touched, writing volume, unfamiliar code, or debugging effort; and note that a `good first issue` label does **not** by itself clear clause (a) or (c) — the umbrella and graveyard cases in this set both carry one. | required |
| actionable | Issue body and discussion thread | The requested outcome is concrete enough that a contributor can determine what needs to change. For bugs, reproduction information or clear expected/actual behavior is sufficient. For documentation, maintenance, or small feature tasks, a specific target and desired outcome are sufficient. A bug report that names the specific missing or broken behavior is also sufficient, even without reproduction steps, when the opener is a maintainer or collaborator or the issue carries a maintainer-applied difficulty label. | required |
| policy | Issue body, discussion thread, and the repository contribution policy quoted in `repo-facts` | The issue must comply with the repository's explicit contribution rules. In particular, if the contribution policy explicitly prohibits AI-generated code or documentation, the issue fails this check. A policy that permits generative-AI tools subject to human responsibility does not by itself fail the check. Also reject issues that require automated bulk changes, unauthorized third-party dependencies, unvetted architectural refactors, or other work explicitly prohibited by repository rules. | required |



## Verdict rule

<!-- State how the grades above combine into accept or reject, and how
unclear is treated. Example shape (write your own): "accept if every
required check passes; preferred checks never change the verdict, they
rank accepted issues; unclear counts as fail." -->

* **Accept:** An issue is marked as **accept** if and only if **ALL required checks** evaluate to `pass`.
* **Reject:** An issue is marked as **reject** if **ANY required check** evaluates to `fail` or `unclear`.
* **Preferred Checks:** Preferred checks do not change the `accept`/`reject` verdict. They are used solely to rank accepted issues (issues with more passing preferred checks rank higher).
