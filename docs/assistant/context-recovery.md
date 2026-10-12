# Context Recovery Protocol

## Purpose

Allow a new conversation to resume G4DNailTime after context exhaustion without shared memory.

## Startup Sequence

1. Read `agent.md`.
2. Read `docs/assistant/project-identity.md`.
3. Read `docs/assistant/language-policy.md`.
4. Read `docs/assistant/behavior.md`.
5. Read `docs/assistant/repository-policy.md`.
6. Read `docs/assistant/external-tools-policy.md`.
7. Read `docs/assistant/autonomous-operation.md`.
8. Read `docs/assistant/critical-review.md`.
9. Read `docs/assistant/tdd-policy.md`.
10. Read `docs/assistant/session-state.md`.
11. Read `docs/assistant/memory/current-context.md`.
12. Read `docs/assistant/memory/next-handoff.md`.
13. Read `docs/prompts/_common.md`.
14. Read the active stage prompt.
15. Read only lifecycle artifacts/code/tests needed for current scope.

## Mandatory Refresh Command

The exact phrase:

`Atualizei o GitHub do NailTime.`

forces this startup/recovery process again against a fresh repository snapshot.

No confirmation is required.

## Recovery State

Establish:
- current lifecycle stage;
- active REQs;
- active TASKs;
- active TESTs;
- last verified repository state;
- last verified TDD state;
- accepted decisions;
- blockers;
- next permitted action.

If a required item is unknown and blocks work, ask in `pt-BR`.

## State Is Not Memory

Never rely on undocumented previous-chat memory.

Repository artifacts are authoritative.

## Context Snapshot

At stable checkpoints, propose updates to:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/assistant/memory/improvement-backlog.md` when needed.

Do not store private chain-of-thought.
