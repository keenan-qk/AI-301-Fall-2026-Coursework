# Plan for Issue #73

## Diagnosis

The Quick Start environment instructions are inconsistent with the example environment configuration.

At the reproduced commit `f89c06fc3ff292df2a04a39ac51319d32a76b779`, `README.md:24-25` tells users to copy `.env.example` to `.env` and add `OPENROUTER_API_KEY`. However, `.env.example:16-19` does not contain `OPENROUTER_API_KEY` and documents only `mock` and `openai` as `LLM_PROVIDER` options.

The reproduction also confirmed that `core/config.py:18-22` declares `openrouter_api_key`, `openrouter_base_url`, and `openrouter_model` settings. This establishes that the example environment file is missing configuration fields that the README tells the user to supply. The reproduction did not establish whether application code actually uses the OpenRouter settings.

## Scope

### In scope

- Update `.env.example` so it contains the `OPENROUTER_API_KEY` variable referenced by the README Quick Start instructions.
- Add an `OPENROUTER_API_KEY` example placeholder alongside the existing API-key configuration.
- Leave the existing `mock` and `openai` `LLM_PROVIDER` options unchanged because repository inspection shows no OpenRouter provider path is currently wired.
- Keep the change limited to correcting the environment configuration example.

### Not in scope

- Changing LLM provider implementation behavior.
- Adding or wiring an OpenRouter `LLM_PROVIDER` implementation.
- Refactoring `core/config.py` or unrelated configuration code.
- Changing model defaults or provider behavior.
- Unrelated README or `.env.example` cleanup.
## Files to touch

- `.env.example` — align the example LLM environment configuration with the repository's existing OpenRouter settings and the README Quick Start instructions.


## Approach

1. Verify the existing provider handling and configuration against the reproduction evidence. Repository inspection shows that OpenRouter settings are declared in `core/config.py`, but no OpenRouter `LLM_PROVIDER` path is currently wired.
2. Update the LLM section of `.env.example` by adding an `OPENROUTER_API_KEY` placeholder so the example contains the environment variable referenced by the README Quick Start.
3. Leave the existing `LLM_PROVIDER` options comment listing `mock` and `openai` unchanged; repository inspection found no code path that selects OpenRouter through `LLM_PROVIDER`.
4. Compare the resulting `.env.example` with the README Quick Start and `core/config.py` to verify that the missing environment-variable example has been corrected without documenting unsupported provider behavior.
5. Avoid implementation, configuration, or documentation changes beyond what is necessary to resolve the reproduced mismatch.

## Test plan

1. Repeat the original reproduction comparison against `README.md`, `.env.example`, and `core/config.py`.
2. Confirm that the README Quick Start instruction to add `OPENROUTER_API_KEY` now corresponds to an `OPENROUTER_API_KEY=` entry in `.env.example`.
3. Confirm that the existing `LLM_PROVIDER` documentation still lists `mock` and `openai` and has not been expanded to claim an unsupported OpenRouter provider path.
4. Confirm that the existing `OPENAI_API_KEY` example and other LLM configuration remain unchanged.
5. Review the final diff to verify that no unrelated configuration or documentation changes were introduced.

Expected result: `.env.example` contains an `OPENROUTER_API_KEY=` example entry matching the variable referenced by the README Quick Start, while the existing `mock` and `openai` provider documentation remains unchanged.

## Risks and unknowns

Repository inspection shows that OpenRouter settings are declared in `core/config.py`, but the existing provider handling does not currently expose an OpenRouter `LLM_PROVIDER` path. This plan does not attempt to implement or document one.

The change therefore addresses only the reproduced environment-example mismatch: the README tells users to add `OPENROUTER_API_KEY`, while `.env.example` currently omits that variable. Any work to wire OpenRouter into provider selection would be a separate implementation change outside the scope of this issue plan.

## Deviations

No deviations. The implementation followed the accepted plan: `.env.example` was updated with an `OPENROUTER_API_KEY=` placeholder, while the existing `LLM_PROVIDER` options and provider implementation were left unchanged.
