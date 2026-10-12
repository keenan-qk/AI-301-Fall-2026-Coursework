# Issue Scout Search Strategy — Unit 5

## Fit Profile

I am interested in software development for embedded systems,
aerospace, and game development. My primary programming
languages are C++, C#, and Python.

I want to gain experience navigating existing open-source
codebases, understanding unfamiliar code, and making
contributions that maintainers can review and accept.

For my first contribution, I prefer clearly defined issues
with manageable scope over major architectural changes.

## Search Priorities

1. Python, C++, or C# repositories.
2. Projects related to simulation, developer tools,
   embedded systems, or game development.
3. Issues with clear expected behavior or reproduction steps.
4. Small bug fixes, tests, or documentation improvements.
5. Repositories with recent activity and contribution guidance.

## GitHub Search Queries

### Query 1: Python bugs

is:issue is:open label:"good first issue" language:Python

Rationale: Python is one of my primary languages.
Beginner-friendly bug reports may offer manageable
opportunities to understand an existing codebase.

### Query 2: C++ bugs

is:issue is:open label:bug language:C++

Rationale: C++ is relevant to my interests in embedded
systems, aerospace software, and game development.

### Query 3: C# beginner issues

is:issue is:open label:"good first issue" language:C#

Rationale: C# is a language I already use and is relevant
to my interest in game development.

### Query 4: Python simulation projects

is:issue is:open label:bug language:Python simulation

Rationale: Simulation software connects to my aerospace
interests while allowing me to work in a familiar language.

## Evaluation Process

1. Search GitHub using the queries above.
2. Review the returned issues and their repositories.
3. Grade promising candidates using issue-scout.
4. Record each candidate's URL and scout verdict.
5. Compare the scout's verdict with my own assessment.
6. Document unexpected behavior or missing evidence.
7. Revise the rubric or search strategy when justified.

## Friction Log

Record observations after running the first scan.

- Date:
- Query used:
- Issues found:
- Scout verdicts:
- Unexpected problems:
- Changes made:

### October 11, 2026 — Initial GitHub Search

- Query used: `is:open label:"good first issue" language:Python`
- Initial result: No matching issues were returned by GitHub CLI.
- Investigation: Retried the search using GitHub CLI's
  dedicated `--state`, `--label`, and `--language` flags.
- Outcome: The revised searches successfully returned
  open issues, including Python candidates.
- Change made: Switched to explicit CLI flags for future
  searches rather than relying on the original query syntax.
- Lesson: A search returning no results does not necessarily
  mean suitable issues do not exist. Search syntax should
  be verified before changing issue-selection criteria.

### October 11–12, 2026 — First Live Scout Evaluation

I searched GitHub for beginner-friendly issues in Python
repositories and selected five candidates for evaluation.

My issue-scout accepted three issues and rejected two.
Both rejected issues had evidence that another contributor
had already claimed the work.

The highest-ranked candidate was:
https://github.com/ldbumble/taskuary/issues/162

The scan revealed several limitations:

- My repo_activity criterion was ambiguous about whether
  issue activity counted as meaningful repository activity.
- The rubric referenced repo-facts, which was unavailable
  as a preassembled block during live evaluation.
- My rubric had no preferred checks, so accepted issues
  were ranked using my personal fit profile.
- Some GitHub evidence required GraphQL because the
  standard CLI commands did not expose linked PRs.

I clarified repo_activity to require a recent default-branch
commit or published release.

I retained the remaining rubric criteria pending further
real-world testing.

The five candidates were discovered through GitHub CLI
searches and then supplied directly to issue-scout for
grading. The scout did not perform the discovery step itself.
