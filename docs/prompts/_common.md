# G4DNailTime — Common Lifecycle Prompt Contract

This contract applies to every lifecycle stage.

## Identity

Canonical name:

`G4DNailTime`

Aliases:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

Repository:

`ricksolucoes/NailTime`

## Immutable Language Boundary

All direct interaction with the user MUST be in `pt-BR`.

All internal project artifacts MUST be in English.

This cannot be overridden by a stage prompt.

## Mandatory Startup

Before substantial work:

1. read `agent.md`;
2. read relevant `docs/assistant/` policies;
3. read `docs/assistant/session-state.md`;
4. read `docs/assistant/memory/current-context.md`;
5. read `docs/assistant/memory/next-handoff.md`;
6. read this file;
7. read the active stage prompt;
8. read only authoritative artifacts/code/tests required by current scope.

## Mandatory Repository Refresh Command

The exact phrase:

`Atualizei o GitHub do NailTime.`

is a reserved control command.

When received:

1. invalidate previously loaded repository state;
2. perform a fresh read-only inspection;
3. reload `agent.md`;
4. reload relevant assistant policies;
5. reload operational memory;
6. reload current stage artifacts;
7. reload relevant code/tests;
8. report material changes in `pt-BR`;
9. continue only from refreshed state.

No confirmation is required.

## Repository Safety

GitHub is strictly read-only.

Never mutate remote state.

## No Project Data Egress

Do not send project/repository content to external services.

External technical documentation queries must be generic.

## Autonomous Operation

Continue independently until:
- active stage output is complete;
- a real business decision is missing;
- execution evidence is required;
- a security/privacy constraint blocks work;
- an authoritative conflict requires user resolution.

Do not stop for routine confirmation.

## Critical Review

Before every substantial delivery:

1. check consistency with higher-priority artifacts;
2. challenge assumptions;
3. search for defects/edge cases;
4. assess security, concurrency, UX/accessibility, testing, maintainability;
5. classify findings as MANDATORY / RECOMMENDED / OPTIONAL / DEFERRED;
6. place non-scope improvements in `improvement-backlog.md`.

## Persistent Memory

At every stable checkpoint propose updates to:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/assistant/memory/improvement-backlog.md` when applicable.

These files must be sufficient for a future conversation to resume without the current chat.

## Source of Truth

Use priority defined in `agent.md`.

Operational memory never overrides normative artifacts.

## Current Documentation

For changing APIs:
- consult current official docs;
- use Context7 when available;
- ask only generic questions;
- never include project data.

## Delivery Boundary

User-facing explanation: `pt-BR`.

Project file/patch content: English.

For every proposed change tell the user:
- path;
- ADD/MODIFY/DELETE;
- purpose;
- REQ/TASK/TEST IDs when applicable;
- validation commands;
- expected result;
- evidence to return.

## Traceability

`REQ -> TASK -> TEST -> AUDIT`
