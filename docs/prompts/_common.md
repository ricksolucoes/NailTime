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

## Mandatory Startup

Before substantial work:

1. read `agent.md`;
2. read `docs/assistant/repository-sync.md`;
3. read `docs/assistant/session-state.md`;
4. read `docs/assistant/memory/current-context.md`;
5. read `docs/assistant/memory/next-handoff.md`;
6. read this file;
7. determine active lifecycle stage;
8. read the active stage prompt;
9. read only artifacts/code/tests required by active scope.

Load additional assistant policies only when relevant.

## Incremental Repository Synchronization

The exact phrase:

`Atualizei o GitHub do NailTime.`

is a reserved synchronization command.

When received:

1. read current branch/HEAD;
2. read last verified SHA;
3. select sync mode:
   - `NO_CHANGE`
   - `INCREMENTAL`
   - `BASELINE`
   - `FULL_RECOVERY`
4. for `INCREMENTAL`, inspect only the commit/diff range from last verified SHA to current HEAD;
5. classify changed files by impact;
6. reload only changed and directly affected context;
7. record unrelated changed files without loading them unnecessarily;
8. update working repository snapshot;
9. report synchronization summary in `pt-BR`;
10. continue from refreshed state.

Do not re-read the entire repository unless FULL_RECOVERY is actually required.

## Repository Safety

GitHub is strictly read-only.

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

Before substantial delivery:

1. check consistency with higher-priority artifacts;
2. challenge assumptions;
3. search for defects/edge cases;
4. assess security, concurrency, UX/accessibility, testing, maintainability;
5. classify findings as MANDATORY / RECOMMENDED / OPTIONAL / DEFERRED;
6. place non-scope improvements in `improvement-backlog.md`.

## Persistent Memory

At stable checkpoints propose updates to:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/assistant/memory/improvement-backlog.md` when applicable.

Memory must contain the last verified SHA so future sync can be incremental.

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

## Traceability

`REQ -> TASK -> TEST -> AUDIT`
