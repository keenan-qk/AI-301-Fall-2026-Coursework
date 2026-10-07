# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

**GitHub username**

keenan-qk

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-s1/issues/73#issuecomment-6029971353

I reproduced the configuration mismatch at `f89c06f`. The Quick Start tells users to add `OPENROUTER_API_KEY` after copying `.env.example`, but `.env.example` does not include that variable and currently documents only `mock` and `openai` as `LLM_PROVIDER` options.

I plan to update `.env.example` with an `OPENROUTER_API_KEY` placeholder so it contains the variable referenced by the Quick Start. Repository inspection shows that `llm_provider` in `core/config.py` is not consumed elsewhere and that no code path currently selects OpenRouter through `LLM_PROVIDER`, so I will leave the existing `mock` and `openai` provider options unchanged rather than documenting unsupported behavior.

I'll verify the fix by repeating the original comparison and confirming that `.env.example` contains an `OPENROUTER_API_KEY=` entry while the existing `mock` and `openai` provider documentation remains unchanged.

AI disclosure: I used Claude Code and ChatGPT to assist with planning and reviewing this change. I will independently review and verify the implementation and test results.

---

## Your branch

**Branch**

fix/73-env-openrouter-key

**Evidence**

Before, at the reproduced commit `f89c06fc3ff292df2a04a39ac51319d32a76b779`, I compared the Quick Start, `.env.example`, and `core/config.py`.

The README showed:

```text
# Configure environment (add your OPENROUTER_API_KEY to .env)
cp .env.example .env
```

The corresponding `.env.example` section showed:

```text
# LLM provider
# Options: "mock" (default, no API key needed), "openai"
LLM_PROVIDER=mock
OPENAI_API_KEY=sk-your-key-here
```

There was no `OPENROUTER_API_KEY` entry.

`core/config.py` showed:

```text
llm_provider: str = Field(default="mock")
openai_api_key: str = Field(default="")
openrouter_api_key: str = Field(default="")
openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
openrouter_model: str = Field(default="google/gemma-3-27b-it:free")
```

After implementing the change, I reran the comparison.

Command:

```bash
grep -n -A 6 -B 2 "Configure environment" README.md
```

Output:

```text
22-cd pathreview
23-
24:# Configure environment (add your OPENROUTER_API_KEY to .env)
25-cp .env.example .env
26-
27-# Start backing services — must be running before make setup
28-docker compose up -d
29-
30-# Run first-time setup (installs deps, runs migrations, seeds DB, installs frontend)
```

Command:

```bash
grep -n -A 6 "# LLM provider" .env.example
```

Output:

```text
16:# LLM provider
17-# Options: "mock" (default, no API key needed), "openai"
18-LLM_PROVIDER=mock
19-OPENAI_API_KEY=sk-your-key-here
20-OPENROUTER_API_KEY=
21-
22-# App settings
```

Command:

```bash
grep -n -A 6 "llm_provider" core/config.py
```

Output:

```text
18:    llm_provider: str = Field(default="mock")
19-    openai_api_key: str = Field(default="")
20-    openrouter_api_key: str = Field(default="")
21-    openrouter_base_url: str = Field(default="https://openrouter.ai/api/v1")
22-    openrouter_model: str = Field(default="google/gemma-3-27b-it:free")
23-
24-    # Application
```

The after evidence shows that `.env.example` now contains the `OPENROUTER_API_KEY=` entry referenced by the README, while the existing `mock` and `openai` provider documentation and `OPENAI_API_KEY` entry remain unchanged.

## Eval iterations

**Run history**

1. Initial complete scored run:

   `agreement: 17/20 scored items`

   All three disagreements were clear-accept packages (`pkg-02`, `pkg-05`, and `pkg-14`). Every reject category matched its gold labels.

2. I revised the `executable` and `uncertainty` checks after analyzing those disagreements. I then ran a canary set with:

   `--only pkg-02,pkg-05,pkg-14,pkg-10,pkg-17,pkg-18,pkg-01,pkg-07`

   I ran this canary twice. Both runs agreed on 7/8 packages. `pkg-02` and `pkg-05` accepted as expected, while the unbuildable packages `pkg-10`, `pkg-17`, and `pkg-18` and wrong-cause packages `pkg-01` and `pkg-07` continued to reject. `pkg-14` continued to reject.

3. Final complete scored run:

   `agreement: 19/20 scored items  (bar: 18/20: PASS)`

   Category results:

   `clear-accept 6/7` 
   `scope-creep 4/4` 
   `thread-convention 2/2` 
   `unbuildable 3/3` 
   `wrong-cause 4/4`

**Package analysis**

I focused on `pkg-05`, a clear-accept package. My initial rubric decided reject while the gold label was accept. The `uncertainty` check treated an implementation detail about a cache file's stored timestamp as an unsupported factual claim, even though that detail could be confirmed by reading the named implementation file and did not undermine the supported diagnosis or fix direction.

I revised the check to distinguish unresolved facts that could change the diagnosis or fix direction from implementation details that a developer would normally confirm while working in the named file. After the revision, `pkg-05` changed to accept and matched its gold label in the canary runs and the final complete run.

**Check rationale**

The revised `uncertainty` check in `rubric.md` is:

> Claims that the diagnosis or fix direction depends on are supported by the available evidence. Unresolved facts that would change the diagnosis or fix direction are identified as risks or unknowns. Implementation details a developer would confirm by reading the named file, such as where a timestamp is stored, do not fail this check.

I revised this check because the earlier version was too strict about implementation details that were not material to whether the proposed diagnosis and fix direction were justified. `pkg-05` exposed that problem. The revised wording still requires evidence for claims that the diagnosis or fix depends on, but does not reject an otherwise executable plan merely because a developer must confirm a local implementation detail while reading the code.

**Trade-offs**

Loosening `executable` and `uncertainty` risked allowing genuinely unbuildable or wrong-cause plans to pass. I therefore canaried the revisions against `pkg-10`, `pkg-17`, and `pkg-18` from the unbuildable category and `pkg-01` and `pkg-07` from the wrong-cause category, alongside the clear-accept packages I was trying to fix.

Across two canary runs, those five reject packages continued to reject, while `pkg-02` and `pkg-05` accepted. `pkg-14` continued to reject because it states its stdin-wiring mechanism as fact before tracing it. Its gold label is accept, but its gold note describes the case as arguable. I accepted that remaining miss rather than loosening the diagnosis or uncertainty checks further and risking false accepts in the wrong-cause category.

The final complete run scored 19/20, with every reject category at 100% agreement.
