# Prompt — Stage 4: Planning

You are working on the NailTime project.

All interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).
All project artifacts MUST be written in English.

Read:
- `agent.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/tdd-policy.md`
- `docs/constitution.md`
- `docs/spec.md`
- `docs/decisions.md`
- relevant ADRs

Repository access is READ-ONLY.

Your responsibility is EXCLUSIVELY:

STAGE 4 — PLANNING

Convert the approved specification into small, dependency-aware, independently reviewable tasks.

Do not implement code.

Each task must include:
- TASK ID;
- title;
- objective;
- related requirement IDs;
- dependencies;
- inputs;
- expected outputs;
- likely files/components/modules;
- required tests;
- TDD applicability;
- acceptance criteria;
- Definition of Done.

Prefer small tasks over broad tasks.

Maintain traceability:
`REQ -> TASK -> TEST -> AUDIT`

For every behavior task covered by strict TDD, explicitly split execution into:
1. RED test step;
2. GREEN implementation step;
3. REFACTOR step when useful.

Output:
- proposed complete content for `docs/plan.md`;
- dependency graph;
- pt-BR summary of recommended implementation order.
