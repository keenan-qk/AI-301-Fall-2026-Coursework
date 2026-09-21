# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73

**Verdict output**

Live-mode run of `issue-select` against the rubric now in `tools/issue-select/rubric.md`
(sha256 `c5aee4645b6410e8`, the same rubric fingerprinted in `eval-run.txt`).

````
Scope check: candidate is in `codepath/pathreview-ai301-fa26-s1`, the repo named in
scope.md. The Path Review house rule (classmate claim comments do not block) was
available but never applied: this issue has no comments at all.

maintainer_activity  pass
repo_activity        pass
unassigned           pass
newcomer_scope       pass
actionable           pass
policy               pass

All six required checks pass. The rubric defines no preferred checks.

Fit: strong. Python repo, explicitly bounded requirements, two named files, no
architectural decisions. Exercises the contribution workflow (fork, branch naming,
the five CI jobs, PR template) without requiring prior knowledge of the codebase.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73",
  "checks": [
    {"name": "maintainer_activity", "grade": "pass",
     "evidence": "Maintainer Aburke225 committed to main on 2026-09-16 and applied this issue's four labels on 2026-09-16, 4 days before the 2026-09-20 grading date."},
    {"name": "repo_activity", "grade": "pass",
     "evidence": "Repo not archived; last push 2026-09-16T21:48:27Z, with 3 of the last 5 default-branch commits dated 2026-09-16."},
    {"name": "unassigned", "grade": "pass",
     "evidence": "assignees is empty, the issue has zero comments, the timeline shows only four label events, and `gh pr list --state all` returns [] for the whole repo."},
    {"name": "newcomer_scope", "grade": "pass",
     "evidence": "Fires no disqualifying clause: no separate issue numbers or ongoing-contribution language (a), core ask 'Make the two files agree' is stated not proposed (b), zero linked PRs and zero prior claimants (c), and the change is documentation/config-example only, not a new user-facing tool (d)."},
    {"name": "actionable", "grade": "pass",
     "evidence": "Body gives the concrete target and desired outcome: README tells you to add OPENROUTER_API_KEY but .env.example omits it and lists only mock/openai for LLM_PROVIDER while core/config.py defines both - 'Make the two files agree.'"},
    {"name": "policy", "grade": "pass",
     "evidence": "docs/CONTRIBUTING.md states no AI-contribution restriction; its only prohibitions are 'Never run ruff check --fix --unsafe-fixes' and not removing deliberate '# noqa' comments, neither of which this docs fix involves."}
  ],
  "verdict": "accept"
}
````

---

## Eval iterations

**Run history**

1. `17/20` — full run, rubric as first written (below the bar).
2. `5/7` — `--only issue-05,issue-15,issue-20,issue-10,issue-01,issue-04,issue-06`
   after rewriting `newcomer_scope`. Fixed the three scope misses but broke two
   clear-accepts.
3. `6/7` — same `--only` set after tightening clauses (a) and (d). issue-01
   recovered; issue-04 still failed, now on `actionable` alone.
4. `1/1` — `--only issue-04` after adding a sufficient condition to `actionable`.
5. `20/20` — full run. Matches the committed `eval-run.txt`:
   `agreement: 20/20 scored items  (bar: 18/20: PASS)`

**Issue analysis**

`issue-05` (sympy/sympy#28806). My rubric's decision: **reject**. Gold label:
**reject** (`"codebase-wide type-annotation umbrella wearing a good-first-issue
label"`). Under my first rubric this issue was graded **accept** — one of the three
misses that produced 17/20.

The reasoning that produces the reject is clause (a) of `newcomer_scope`. The body is
an open-ended invitation rather than a task: `"this issue is about incrementally
adding more type annotations"` and `"PRs are welcome both big and small (better to
start small)"`. There is no finished state, so the issue never closes. The repo-facts
line confirms the issue is a stream, not a unit: twelve linked PRs, of which five are
already merged (`sympy/sympy#28807 (merged); sympy/sympy#28813 (merged); ...`). The
maintainer explicitly refuses to define a unit of work for any one contributor:
`"Part of the idea of this issue as a good first issue is that it encourages people to
go and look through the codebase which is an important part of learning to contribute.
Have a look around yourself and see what you can find."` and `"We don't generally
assign issues in SymPy. Anyone can work on this."`

My original rubric missed it because that check only failed an issue that
`"explicitly requires a repository-wide refactor"` — and this issue never says so. It
wears `Easy to Fix` and `good first issue` instead.

**Check rationale**

The `newcomer_scope` check as currently written in `tools/issue-select/rubric.md`:

> | newcomer_scope | Issue body, labels, comment thread, and the `this issue: assignees / linked PRs` line in the repo-facts block | The issue is **one unit of work whose finished state the issue itself already fixes**. Fail if any of: **(a) Umbrella or stream** — the body references 2 or more separate issue numbers as the work items, or invites ongoing/repeated contribution over time ("incrementally", "PRs welcome big and small", "megaissue"), or repo-facts shows 3 or more linked PRs already merged against it, or the thread shows contributors each claiming a different sub-target. An enumerated list of files, pages, or same-kind items that a single PR would land together does **not** fire this clause, however long, and a trailing "etc." in such a list does not make it open-ended. **(b) Unsettled core** — the issue's *primary* deliverable is still proposed rather than decided, and no maintainer comment settles it: hedging on the core ask ("perhaps we could", "likely surface", "TBD", "out of scope for v1"), a target behavior taken from an unverified or contradicted external spec, or a required asset/product decision the issue says does not exist yet. A hedge confined to an item the issue itself marks optional or lower-priority does not fire this clause. **(c) Abandoned-attempt history** — 2 or more linked PRs are closed unmerged, or the thread shows 3 or more prior claimants who did not finish. **(d) New feature surface** — the issue asks for a new user-facing tool, element, command, or endpoint **in the application** (documentation is excluded), wired across more than one subsystem. Restoring, completing, or extending coverage of a capability the product already has does **not** fire this clause. Otherwise pass. Do not fail for number of files touched, writing volume, unfamiliar code, or debugging effort; and note that a `good first issue` label does **not** by itself clear clause (a) or (c) — the umbrella and graveyard cases in this set both carry one. | required |

Reasoning behind this form. My first version graded only the *size* of the change and
required the issue to say out loud that it was too big. All four scope-category items
are issues that are too big while sounding small, so size-only grading caught one of
four. The rewrite grades two different things instead: whether the issue is **one
unit** (clauses a, c) and whether its **end state is already settled** (clauses b, d).

The negative clauses matter as much as the positive ones. `issue-01` (conda#16475) is
larger than most rejects — a new docs page plus edits to four existing pages — and
gold accepts it, with the note `"docs task with a stated home and scope"`. So file
count cannot be the discriminator, and the "enumerated list ... does **not** fire this
clause" sentence exists specifically to keep it. Likewise the clause (d) carve-out for
`"restoring, completing, or extending coverage"` keeps `issue-04`, a two-line bug
report about previews that are missing for rules the product already supports.

**Trade-offs**

The first draft of this check is a worked example of what it gives up, and I have the
canary runs to prove it. Written without the two carve-outs, it rejected `issue-05`,
`issue-15` and `issue-20` correctly but also flipped `issue-01` and `issue-04` from
accept to reject — `5/7` on the `--only` canary, worse in practice than the 17/20
rubric it replaced, because it traded three scope misses for two clear-accept misses.
Re-running the same `--only` set after adding the carve-outs recovered `issue-01`
(`6/7`), and the check has cost nothing elsewhere: the final full run is `clear-accept
8/8`.

What it still gives up, knowingly: clause (c) rejects on two closed-unmerged linked
PRs or three unfinished claimants, which will also reject a genuinely easy issue that
two people happened to abandon for unrelated reasons. I accept that miss. A first
issue with a graveyard behind it is not worth the risk to a newcomer even when the
graveyard is coincidental, and the cost of the false reject is only that I pick a
different issue.

---

## Selection rationale

1. **Fit to my interests and to the time available.** I selected issue #73 because it is a small, clearly bounded documentation fix involving README.md and .env.example. I prefer a manageable first contribution with clear requirements, and this issue gives me an opportunity to practice navigating an existing open-source project and understanding how its configuration and documentation fit together. The repository also uses Python, which is one of the languages I use, while the skills I am building here are relevant to my broader interest in software development, including embedded/aerospace and game development.

2. **What the verdict established, and what it could not.** The verdict identified that issue #73 is active, unassigned, actionable, policy-compatible, and appropriately scoped for a first contribution. In particular, the issue identifies the two files involved and describes the inconsistency between them, so the expected change is concrete. My selection also reflects the practical fit of the issue: its scope is small enough for a first contribution and gives me a chance to work through an existing repository rather than designing a larger change.

3. **Anticipated difficulty in claiming and defending it.** The main difficulty I anticipate is making sure I understand the repository's configuration well enough to make README.md and .env.example agree correctly. I would need to verify the existing configuration behavior and contribution workflow before making the change, so that I can defend why the resulting documentation is correct. The issue itself is small, but the claiming process still requires enough repository understanding to make a correct contribution.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
