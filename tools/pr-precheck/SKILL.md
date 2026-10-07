---
name: pr-precheck
description: Grade a PR package (a candidate pull request read against the plan it claims to implement and the issue that plan belongs to) and decide whether it is ready to submit. Use when checking your own branch, draft PR title, and description before opening the pull request, or when grading an eval package bundle.
---

# pr-precheck: rubric-driven PR grading

## The question

Grade exactly one PR package to answer one question: is this pull request ready to submit?

A PR package consists of the candidate PR title and description, commits, unified diff, and test evidence, read against the accepted plan, its recorded deviations, and the issue the plan belongs to. Do not grade unrelated artifacts, multiple PR packages at once, or substitute general impressions for the rubric.

## Inputs and modes

In **live mode**, grade the student's own submission. Read `plan.md`, including its deviation notes; obtain the complete branch diff relative to the repository's default branch with `git diff main...HEAD`; read the draft PR title and description; inspect the student's captured test evidence; and read the issue the plan belongs to. Gather issue-side requirements, the PR template, contribution instructions, and stated repository policy from the real repository. For a house-chain student, use the assigned house plan and reproduction pack in place of the student's own earlier artifacts.

In **eval mode**, treat the supplied package bundle as the whole world. Use only facts contained in the bundle. Do not fetch GitHub, inspect a working copy, or use outside information. Grade the complete package by executing every rubric check and the full verdict rule.

## The scope seam (live mode only)

In live mode, read `scope.md` before grading. Use its Repo entry to determine the only repository this tool may operate on and apply the Path Review house rules it contains.

Refuse to grade a live PR targeting any other repository. If the Repo entry still contains its bracketed placeholder, stop without grading and tell the student to fill it with the section's Path Review repository. Never guess the repository.

In eval mode, ignore `scope.md` entirely.

## The voice seam (live mode only)

In live mode, read `voice-guide.md` and check the draft PR title and description against its personal writing rules. Report any broken voice rule in the readable summary and identify the rule that was broken.

Voice-guide compliance does not change the verdict by itself. Only a check defined in `rubric.md` may affect the verdict.

In eval mode, ignore `voice-guide.md` entirely.

## Component reads

Read `rubric.md` for the checks, their evidence requirements, pass conditions, weights, and the verdict rule.

Read `references/evidence-guide.md` as the map for locating each evidence family in a PR package.

Execute `procedure.md` exactly as written. It determines the read order, evidence-gathering steps, check execution, and verdict assembly. If the procedure is silent about a necessary step, report the gap rather than inventing a procedure of your own.

If `rubric.md` contains no filled checks or `procedure.md` contains no substantive steps, refuse to grade. The tool requires both a rubric and a procedure.

## Verdict and output

The verdict is binary: `accept` means the PR is ready to submit; `reject` means hold the PR. Do not emit a third verdict or an "accept with reservations" verdict.

A short readable per-check summary may appear before the machine-readable result. End every completed grading response with the following fenced JSON block. It must be valid, must preserve this schema, and nothing may appear after it.

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {"name": "<check name>", "grade": "pass|fail|unclear",
     "evidence": "<one line: the fact or quote that decided it>"}
  ],
  "verdict": "accept|reject"
}
