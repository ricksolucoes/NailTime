# Session State

> Compact continuation checkpoint.
> Store only accepted/verified facts.
> Do not store chain-of-thought.

## Project

- Canonical name: `G4DNailTime`
- Aliases: `NailTime`, `RickNailTime`
- Repository: `ricksolucoes/NailTime`

## Lifecycle Stage

`STAGE_1_COMPLETE_PENDING_REPOSITORY_VERIFICATION`

## Current Scope

Constitution acceptance has been recorded in the proposed file set. A fresh read-only repository verification is required before Stage 2 starts.

## Active Requirement IDs

None. Functional requirements have not been created yet.

## Active Task IDs

None.

## Active Test IDs

None.

## Last Verified Repository State

- Branch: `main`
- Commit/SHA before manual Stage 1 application: `c2530891f0210cbad82eca985cd3332e46d4341c`
- Verification date: `2026-10-12`
- At that verified snapshot, `docs/constitution.md` was absent.

## Constitution State

- Proposed repository status after manual application: `ACCEPTED`
- User approval is required before applying this accepted package.
- Fresh repository verification remains mandatory.

## Last Verified TDD State

- RED: not started
- GREEN: not started
- REFACTOR: not started

## Open Questions / Blockers

- Fresh read-only verification of the manually applied accepted Constitution.

## Next Permitted Action

After the user applies this accepted file set and reports the repository update, refresh `ricksolucoes/NailTime`. If `docs/constitution.md` is present with `Status: ACCEPTED` and no higher-priority conflict exists, load `docs/prompts/02-specification.md` and begin Stage 2.

## Files That Must Be Read Next

- `agent.md`
- relevant `docs/assistant/` policies
- `docs/constitution.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/prompts/_common.md`
- `docs/prompts/00-resume.md`
- `docs/prompts/02-specification.md` after acceptance verification
