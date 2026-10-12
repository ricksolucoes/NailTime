# G4DNailTime — Stage 2: Specification

## Responsibility

Perform EXCLUSIVELY:

`STAGE 2 — SPECIFICATION`

## Inputs

Read:
- `agent.md`
- `docs/prompts/_common.md`
- relevant assistant policies/memory
- `docs/constitution.md`
- relevant accepted ADRs
- `docs/decisions.md` if present

## Objective

Transform approved product vision and Constitution into precise, testable functional requirements.

Do not implement code.

Do not create implementation microtasks.

Do not silently resolve ambiguous business rules.

## Coverage

Specify public/admin behavior including:
- normal flows;
- alternate flows;
- loading;
- empty states;
- errors;
- validation;
- permissions;
- accessibility-relevant behavior;
- responsive behavior where functionally relevant.

Initial nail/manicure services are seed/example data, not permanent hardcoded behavior.

## Requirement IDs

Use stable domains such as:
- `REQ-AUTH-*`
- `REQ-APT-*`
- `REQ-AVL-*`
- `REQ-SRV-*`
- `REQ-GAL-*`
- `REQ-BRD-*`
- `REQ-ADM-*`
- `REQ-CST-*`

## Requirement Format

Each requirement:
- ID
- title
- description
- actors
- preconditions
- main flow
- alternate flows
- business rules
- validation/error behavior
- Given/When/Then acceptance criteria

## Ambiguity

Place unresolved matters under:

`Questions for Clarification`

Do not guess.

## Critical Self-Review

Before delivery:
- search for contradictions;
- identify missing states;
- identify race/concurrency implications;
- check historical data semantics;
- check privacy/security implications;
- check whether acceptance criteria are executable/testable;
- identify unnecessary scope.

## Output

Produce proposed English content for:
- `docs/spec.md`

Also propose updated memory/handoff files.

Explain unresolved decisions and required review in `pt-BR`.

Do not write to GitHub.
