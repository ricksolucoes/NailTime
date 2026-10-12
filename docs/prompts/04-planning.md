# G4DNailTime — Stage 4: Planning

## Responsibility

Perform EXCLUSIVELY:

`STAGE 4 — PLANNING`

## Inputs

Read:
- governing policies;
- operational memory;
- Constitution;
- Specification;
- Decisions;
- relevant accepted ADRs.

Proceed only when blocking clarification is sufficiently resolved.

## Objective

Convert approved requirements into small dependency-aware independently reviewable implementation tasks.

Do not implement code.

## Task Format

Each TASK:
- TASK ID
- title
- objective
- related REQ IDs
- dependencies
- inputs
- expected outputs
- likely files/modules
- required tests
- TDD applicability
- acceptance criteria
- Definition of Done

Prefer small verifiable tasks.

## TDD Planning

Behavior tasks must preserve:

1. RED test step
2. valid RED evidence
3. GREEN implementation step
4. valid GREEN evidence
5. REFACTOR when useful
6. verification

Planning may describe implementation scope but must not produce production code.

## Critical Self-Review

Before delivery:
- detect tasks that are too large;
- detect unnecessary dependency chains;
- identify risky sequencing;
- identify missing test infrastructure;
- identify migration/data risks;
- identify parallelizable work;
- identify opportunities to simplify.

## Output

Produce proposed English:
- `docs/plan.md`

Include dependency graph and intended test coverage.

Also propose updated memory/handoff files and improvement backlog if applicable.

Explain recommended execution order in `pt-BR`.

Do not write to GitHub.
