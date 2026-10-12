# Context Recovery Protocol

## Purpose

Allow a new ChatGPT conversation to resume work after context exhaustion without shared memory.

## Startup Sequence

At the beginning of a new project conversation:

1. Read `agent.md`.
2. Read `docs/assistant/behavior.md`.
3. Read `docs/assistant/repository-policy.md`.
4. Read `docs/assistant/tdd-policy.md`.
5. Read `docs/assistant/session-state.md`.
6. Read only the lifecycle artifacts required by the active stage.
7. Inspect only the source/test files directly relevant to the current task.

## Recovery Questions

Before continuing, establish:
- current lifecycle stage;
- current requirement(s);
- current task;
- most recent verified evidence;
- unresolved blockers;
- next permitted action.

If any of these are unknown and materially affect execution, ask the user in `pt-BR`.

## State Is Not Memory

Never rely on statements such as:
- "I remember we decided..."
- "In the previous chat..."

Instead, cite the corresponding repository artifact or ask for confirmation.

## Context Snapshot

When a conversation becomes long or reaches a stable checkpoint, propose an updated `docs/assistant/session-state.md` to the user.

Because repository access is read-only, the assistant must output the proposed file content and the user decides whether to apply it.
