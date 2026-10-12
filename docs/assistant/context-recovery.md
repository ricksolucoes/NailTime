# Context Recovery Protocol

## Purpose

Allow a new conversation to resume G4DNailTime without shared memory and without loading the whole repository.

## Startup Sequence

1. Read `agent.md`.
2. Read `docs/assistant/project-identity.md`.
3. Read `docs/assistant/language-policy.md`.
4. Read `docs/assistant/repository-policy.md`.
5. Read `docs/assistant/repository-sync.md`.
6. Read `docs/assistant/session-state.md`.
7. Read `docs/assistant/memory/current-context.md`.
8. Read `docs/assistant/memory/next-handoff.md`.
9. Read `docs/prompts/_common.md`.
10. Determine active stage.
11. Read only the active stage prompt and artifacts required for current scope.

Other assistant policies should be loaded when relevant to the current work.

## Repository Synchronization

At conversation startup:

- compare current HEAD with the last verified SHA when available;
- use `NO_CHANGE`, `INCREMENTAL`, `BASELINE`, or `FULL_RECOVERY`;
- prefer incremental diff-based loading;
- do not scan the whole repository without cause.

The exact phrase:

`Atualizei o GitHub do NailTime.`

forces this synchronization immediately.

## Recovery State

Establish:
- current lifecycle stage;
- active REQs;
- active TASKs;
- active TESTs;
- last verified branch/SHA;
- latest repository HEAD;
- sync mode;
- last verified TDD state;
- accepted decisions;
- blockers;
- next action.

## State Is Not Memory

Never rely on undocumented prior-chat memory.

Repository artifacts are authoritative.

## Context Snapshot

At stable checkpoints, propose updates to:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/assistant/memory/improvement-backlog.md` when needed.

Do not store private chain-of-thought.
