# Prompt — Stage 1: Constitution

You are working on the NailTime project.

All interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).
All project artifacts you produce MUST be written in English.

Before working, read from the repository in this order:
1. `agent.md`
2. `README.md`
3. `docs/assistant/behavior.md`
4. `docs/assistant/repository-policy.md`
5. `docs/assistant/context-recovery.md`
6. existing `docs/constitution.md`, if present

The repository is READ-ONLY. Do not create, update, delete, commit, push, open PRs, or perform any remote mutation. Return every proposed artifact to the user for review and manual application.

Your responsibility in this conversation is EXCLUSIVELY:

STAGE 1 — CONSTITUTION

Define the project-wide engineering rules and architectural invariants that later stages must obey.

Do not create detailed functional specifications.
Do not implement code.
Do not create the implementation plan.

Project baseline:
- Product: manicure / nail designer scheduling platform
- Frontend: React + TypeScript + Vite
- Backend: Node.js + TypeScript
- Database: PostgreSQL
- Public area: business presentation, services, gallery, service/date/time selection, booking request
- Admin area: authentication, dashboard, agenda, appointment confirmation/rejection, services, availability, blocking, gallery, visual customization, settings

Mandatory lifecycle:
1. Constitution
2. Specification
3. Clarification
4. Planning
5. Implementation with strict TDD
6. Analysis / Validation

For libraries/frameworks/tools with changing APIs, use Context7 when available and prefer current official documentation.

Define at minimum:
- architectural principles;
- frontend/backend boundaries;
- modular/domain organization;
- server authority over business rules;
- validation;
- authentication and authorization principles;
- error handling;
- date/time/timezone rules;
- scheduling integrity and concurrency;
- database principles;
- upload policy;
- theming/design tokens;
- responsiveness and accessibility;
- test strategy;
- strict TDD rule;
- observability/logging principles;
- Definition of Done;
- prohibited decisions;
- decisions intentionally deferred to later stages.

Do not invent unnecessary product behavior. Mark decisions that do not need to be made yet as `DEFERRED DECISION`.

Output:
- proposed complete content for `docs/constitution.md`;
- a short pt-BR summary for the user explaining what must be reviewed before they add it to the repository.
