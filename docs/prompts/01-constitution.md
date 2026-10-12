# G4DNailTime — Stage 1: Constitution

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- `docs/assistant/project-identity.md`
- `docs/assistant/language-policy.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/external-tools-policy.md`
- `docs/assistant/context-recovery.md`
- `README.md`
- existing `docs/constitution.md`, if present

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 1 — CONSTITUTION`

## Objective

Define project-wide engineering rules, architectural invariants, non-negotiable quality constraints, and decisions that later lifecycle stages must obey.

Do not create detailed functional specifications.

Do not implement code.

Do not create implementation microtasks.

## Product Baseline

G4DNailTime is a manicure/nail designer scheduling platform.

Baseline stack:

- Frontend: React + TypeScript + Vite
- Backend: Node.js + TypeScript
- Database: PostgreSQL

Public area baseline:

- business presentation;
- services;
- gallery;
- service selection;
- date selection;
- available time selection;
- booking request.

Administrative area baseline:

- authentication;
- dashboard;
- agenda;
- appointment confirmation/rejection;
- service management;
- availability management;
- blocking;
- gallery;
- visual customization;
- settings.

Business-facing branding is configurable data and must not be confused with the G4DNailTime product identity.

## Mandatory Lifecycle

1. Constitution
2. Specification
3. Clarification
4. Planning
5. Implementation with strict TDD
6. Analysis / Validation

## Constitution Scope

Define at minimum:

- architectural principles;
- frontend/backend boundaries;
- modular/domain organization;
- server authority over business rules;
- validation principles;
- authentication and authorization principles;
- error-handling principles;
- date/time/timezone rules;
- scheduling integrity and concurrency principles;
- database principles;
- upload/storage policy boundaries;
- theming/design-token principles;
- responsiveness;
- accessibility;
- test strategy;
- strict TDD rule;
- observability/logging principles;
- security/privacy principles;
- dependency/current-documentation policy;
- Definition of Done;
- prohibited decisions/practices;
- decisions intentionally deferred to later stages.

Do not invent unnecessary product behavior.

Mark decisions that do not need to be made yet as:

`DEFERRED DECISION`

## Output

Produce proposed complete English content for:

`docs/constitution.md`

Then provide a concise `pt-BR` review summary explaining:

- the major invariants;
- deferred decisions;
- conflicts found, if any;
- what the user must review before manually applying the file.

Do not write to the repository.
