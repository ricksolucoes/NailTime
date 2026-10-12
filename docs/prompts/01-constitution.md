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

Selected baseline stack:
- backend: NestJS `12.x`;
- data access: Prisma `7.x`;
- database: PostgreSQL;
- frontend: Next.js `16.x`;
- frontend language: TypeScript `7.x`;
- full-system E2E: Playwright `1.64.x`.

Do not silently replace a selected major/minor family with `latest` if that would cross the selected version boundary.

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

## Mandatory Cross-Stage Gates

The Constitution MUST require later stages to resolve, without prematurely selecting storage/auth mechanisms:

1. historical semantics for mutable appointment-related data during Specification/Clarification;
2. product/security semantics for authentication, identity, authorization, recovery, revocation, and audit during Specification/Clarification;
3. technical snapshot and authentication strategies only during Planning after semantics are accepted.

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

Mark intentionally postponed technical matters:

`DEFERRED DECISION`

Do not label mandatory security guarantees or required business semantics as optional merely because their technical mechanism is deferred.

## Critical Self-Review

Before delivery:
- challenge every invariant;
- identify overengineering;
- identify missing security/integrity constraints;
- identify decisions that should remain deferred;
- verify historical semantics are assigned to Stage 2/3 rather than silently postponed to Planning;
- verify authentication product semantics are assigned to Stage 2/3 while technical mechanisms remain deferred;
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
