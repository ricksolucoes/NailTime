# Next Handoff

## Status

`STAGE_1_COMPLETE_PENDING_REPOSITORY_VERIFICATION`

## Next Stage

`STAGE_2_SPECIFICATION` only after accepted Constitution verification.

## Objective

Refresh the authoritative repository after manual application. Verify that `docs/constitution.md` exists with `Status: ACCEPTED`, verify continuity artifacts, and then begin Specification if no conflict exists.

## Required Inputs

- `agent.md`
- relevant `docs/assistant/` policies
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/improvement-backlog.md`
- `docs/prompts/_common.md`
- `docs/prompts/00-resume.md`
- `docs/constitution.md`
- `docs/prompts/02-specification.md` after Stage 1 verification

## Active REQ/TASK/TEST

None.

## Verified Evidence

- Last verified remote repository snapshot before Stage 1 application: `main` at `c2530891f0210cbad82eca985cd3332e46d4341c`.
- Stage detection at that snapshot selected Stage 1 because no Constitution existed.
- The accepted package was prepared locally and does not constitute repository evidence.

## Critical Constraints

- GitHub remains read-only for the assistant.
- User-facing communication remains `pt-BR`.
- Internal project content remains English.
- Do not begin Specification until accepted Constitution status is verified in GitHub.
- Do not create implementation tasks or code during Specification.

## Blockers

Fresh read-only verification of the repository after manual application.

## Next Permitted Action

On the repository update signal, invalidate the old snapshot, re-read the required operating files and accepted Constitution, identify material changes, then load `docs/prompts/02-specification.md` if Stage 1 completion is verified.
