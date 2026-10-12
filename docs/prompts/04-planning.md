# G4DNailTime — Stage 4: Planning

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- relevant files under `docs/assistant/`
- `docs/constitution.md`
- `docs/spec.md`
- `docs/decisions.md`
- relevant accepted ADRs

Proceed only when required clarification decisions are resolved enough for planning.

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 4 — PLANNING`

## Objective

Convert the approved specification into small, dependency-aware, independently reviewable implementation tasks.

Do not implement code.

## Task Requirements

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

Avoid tasks such as:

`Implement scheduling system`

Prefer tasks that isolate one verifiable behavior or infrastructure responsibility.

## Dependency Planning

Provide an explicit dependency graph or ordered dependency structure.

Do not schedule tasks before their prerequisites.

## TDD Planning

For every new behavioral task covered by strict TDD, planning must preserve the execution gates:

1. RED test step;
2. user execution and valid RED evidence;
3. GREEN implementation step;
4. user execution and valid GREEN evidence;
5. REFACTOR step when useful;
6. verification.

Planning may describe future production implementation, but Stage 4 must not produce production code.

## Traceability

Maintain:

`REQ -> TASK -> TEST -> AUDIT`

Every TASK must link to one or more REQ IDs.

Critical rules must identify intended TEST coverage.

## Output

Produce proposed complete English content for:

`docs/plan.md`

Include:

- task definitions;
- dependencies;
- planned test coverage;
- lifecycle checkpoints.

Then provide a `pt-BR` summary explaining the recommended execution order and major dependencies.

Do not write to the repository.
