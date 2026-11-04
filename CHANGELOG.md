# Changelog

All notable changes to MULTITOOL.

## v14 (2026-11-04)
- Real model switching in Claude Code: agents `mt-fast` (Haiku), `mt-worker` (Sonnet) and `mt-deep` (Opus); commands `/multitool-fast` and `/multitool-deep`, which run the whole turn on that model; and the `opusplan` tip.
- Tested with Claude Code 2.1: the `mt-fast` agent ran on Haiku while the main chat ran on Sonnet; `/multitool-fast` ran the whole turn on Haiku.
- In the Claude apps nothing changes: there, a skill can only recommend a model.

## v13 (2026-11-04)
- New 7b "critical check": after key steps (crop, cut list, generation, first render) MULTITOOL measures instead of assuming, looks at the real output, names a concrete defect and fixes its cause.
- Brakes so the check never ruins a result: compare with the previous version and keep the better one, at most 2 fix rounds, respect the user's choices, taste goes to an offered alternative.
- Recipes: measure before cropping; compare graded and ungraded photo.

## v12 (2026-11-04)
- Description rewritten with trigger phrases (English and Russian) and clear "don't use" cases, so MULTITOOL fires when it should and stays quiet otherwise.
- Core file cut from 247 to 157 lines: less context spent on every run.
- Concrete preflight: `ListConnectors`, `get_device_info`, balance calls, `ToolSearch`.
- Honest model routing: advice by task type only; scheduled-task model changed only after the user says yes.
- Stall rule (about 10 calls without progress → re-plan) replaces uncountable call budgets.
- Four worked examples, including one where MULTITOOL should not run.
- Removed: the long cheat-sheet (went stale), the red-flag table (merged into limits), user-specific settings (belong in `my-profile`), the "keep old rules" gate that blocked pruning.
- Recipes: speech-to-text now uses a private upload route instead of a public branch; logo removal marked personal-use only.

- v1–v4 2026-11-03: live-inventory router, ranking rules, cheat-sheet; install suggestions; classification, subagent models, quality loop, safety; Evolution loop with unlazy gates and weekly review.
- v5–v7 2026-11-04: cheat-sheet rows for unlisted plugins; limit budget; situational, value-over-thrift spending.
- v8–v10 2026-11-04: honest model routing; red flags as pause-and-decide; connectors and third-party AI services.
- v11 2026-11-04: companions my-profile and multitool-recipes; preflight; known limits with workarounds (2b); quality bars by output type; spend line after L/paid work; site table and HF recipe moved to recipes.
