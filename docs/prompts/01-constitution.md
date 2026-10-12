# G4DNailTime — Stage 1: Constitution

## Responsibility

Perform EXCLUSIVELY:

`STAGE 1 — CONSTITUTION`

## Inputs

Read:
- `agent.md`
- `docs/prompts/_common.md`
- relevant assistant policies
- README
- existing Constitution if present
- current memory/handoff files

## Objective

Define project-wide engineering invariants and architecture constraints for later stages.

Do not create detailed functional requirements.

Do not implement code.

Do not create implementation microtasks.

## Product Baseline

G4DNailTime is a manicure/nail designer scheduling platform.

Baseline stack:
- React
- TypeScript
- Vite
- Node.js
- TypeScript backend
- PostgreSQL

Public baseline:
- business presentation;
- services;
- gallery;
- service/date/time selection;
- booking request.

Admin baseline:
- authentication;
- dashboard;
- agenda;
- appointment confirmation/rejection;
- service management;
- availability/blocking;
- gallery;
- visual customization;
- settings.

## Define

At minimum:
- architecture principles;
- frontend/backend boundaries;
- domain organization;
- server authority;
- validation;
- auth/authz principles;
- errors;
- dates/timezones;
- scheduling concurrency/integrity;
- database principles;
- upload/storage boundaries;
- theming/design tokens;
- responsiveness;
- accessibility;
- testing;
- strict TDD;
- observability;
- security/privacy;
- dependency/current-doc policy;
- Definition of Done;
- prohibited practices;
- deferred decisions.

Mark intentionally postponed matters:

`DEFERRED DECISION`

## Critical Self-Review

Before delivery:
- challenge every invariant;
- identify overengineering;
- identify missing security/integrity constraints;
- identify decisions that should remain deferred;
- verify no detailed product behavior was invented.

## Output

Produce proposed English content for:
- `docs/constitution.md`

Also propose updated:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/assistant/memory/improvement-backlog.md` if improvements were identified.

Explain to the user in `pt-BR` what to review/apply.

Do not write to GitHub.
