# Context Recovery Protocol

## Purpose

Allow a new ChatGPT conversation to resume G4DNailTime work after context exhaustion or when work intentionally moves to another conversation.

Shared model memory is not required.

## Startup Sequence

At the beginning of a new project conversation:

1. Read `agent.md`.
2. Read `docs/assistant/project-identity.md`.
3. Read `docs/assistant/language-policy.md`.
4. Read `docs/assistant/behavior.md`.
5. Read `docs/assistant/repository-policy.md`.
6. Read `docs/assistant/external-tools-policy.md`.
7. Read `docs/assistant/tdd-policy.md`.
8. Read `docs/assistant/session-state.md`.
9. Read `docs/prompts/_common.md`.
10. Read the prompt for the active lifecycle stage.
11. Read only lifecycle artifacts required by that stage.
12. Inspect only source/test files directly relevant to the current scope.

## Recovery State

Before continuing, establish from repository evidence:

- canonical project identity;
- current lifecycle stage;
- current requirement IDs;
- current task IDs;
- current test IDs;
- most recent verified repository state;
- most recent verified TDD state;
- accepted decisions needed for continuation;
- unresolved blockers;
- next permitted action.

If a required item is unknown and materially affects execution, ask the user in `pt-BR`.

## State Is Not Memory

Never rely on:

- "I remember..."
- "We decided in another chat..."
- "The previous conversation said..."

Use repository artifacts.

If a decision is absent from the authoritative repository artifacts, it is not authoritative.

## Context Snapshot

When a conversation becomes large or reaches a stable checkpoint, propose an updated:

`docs/assistant/session-state.md`

The proposed file is written in English.

Explain the proposed update to the user in `pt-BR`.

Because repository access is read-only, the user decides whether to apply it.
