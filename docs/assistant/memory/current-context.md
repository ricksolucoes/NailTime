# Current Context

> Authoritative compact continuation context.
> Store accepted/verified project state only.
> Do not store private chain-of-thought.

## Project

- Name: `G4DNailTime`
- Repository: `ricksolucoes/NailTime`

## Current Lifecycle Stage

`STAGE_1_COMPLETE_PENDING_REPOSITORY_VERIFICATION`

## Current Objective

Verify the manually applied accepted Constitution, then begin Specification only if the repository confirms Stage 1 completion.

## Active Scope

Stage 1 Constitution acceptance and transition verification.

## Active Requirements

None. Stage 2 has not started.

## Active Tasks

None.

## Active Tests

None.

## Accepted Decisions Relevant Now

- Canonical product name: `G4DNailTime`.
- Repository: `ricksolucoes/NailTime`.
- GitHub access for the assistant is read-only.
- User interaction is `pt-BR`.
- Internal project artifacts are English.
- Baseline stack family: React + TypeScript + Vite, Node.js + TypeScript, PostgreSQL.
- Mandatory lifecycle: Constitution -> Specification -> Clarification -> Planning -> Implementation with strict TDD -> Analysis / Validation.
- Strict TDD sequence: `REQ -> TASK -> TEST -> RED -> GREEN -> REFACTOR -> AUDIT`.
- Constitution content has been explicitly approved by the user if and only if this accepted package is manually applied.

## Constitution State

- Target file: `docs/constitution.md`
- Intended applied status: `ACCEPTED`
- Repository verification: pending

## Last Verified Repository Snapshot

- Branch: `main`
- Commit/SHA before manual Stage 1 application: `c2530891f0210cbad82eca985cd3332e46d4341c`
- Verified date: `2026-10-12`
- At that snapshot, `docs/constitution.md` was absent.

## Last Verified Execution Evidence

Repository inspection only. Implementation has not started.

## Current TDD Gate

`NOT_STARTED`

## Current Blockers

Fresh read-only repository verification after the accepted Stage 1 files are manually applied.

## Next Permitted Action

Refresh the authoritative repository. If Constitution acceptance is verified, load Stage 2 and create only Specification-stage artifacts.

## Required Files for Continuation

- `agent.md`
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/prompts/_common.md`
- `docs/prompts/00-resume.md`
- `docs/constitution.md`
- `docs/prompts/02-specification.md` after acceptance verification
