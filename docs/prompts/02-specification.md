# G4DNailTime — Stage 2: Specification

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- relevant files under `docs/assistant/`
- `docs/constitution.md`
- accepted ADRs relevant to product behavior
- `docs/decisions.md` if it already contains accepted decisions

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 2 — SPECIFICATION`

## Objective

Transform the approved constitution and product vision into precise, testable functional requirements.

Do not implement code.

Do not create technical implementation microtasks.

Do not silently resolve ambiguous business rules.

## Functional Coverage

Specify the public and administrative experiences, including:

- normal states;
- alternate flows;
- empty states;
- loading states;
- error states;
- validation states;
- permission/authorization states;
- accessibility-relevant behavior;
- responsive behavior where functionally relevant.

The initial manicure/nail service catalog is seed/example data, not hardcoded permanent behavior.

The administrator must be able to create and manage services according to the approved product rules.

## Requirement Identifiers

Use stable domain identifiers such as:

- `REQ-AUTH-*`
- `REQ-APT-*`
- `REQ-AVL-*`
- `REQ-SRV-*`
- `REQ-GAL-*`
- `REQ-BRD-*`
- `REQ-ADM-*`
- `REQ-CST-*`

Do not renumber existing accepted requirements without a documented reason.

## Requirement Format

For every requirement include:

- ID;
- title;
- description;
- actors;
- preconditions;
- main flow;
- alternate flows;
- business rules;
- validation/error behavior;
- acceptance criteria using Given / When / Then.

## Ambiguity

Place unresolved matters under:

`Questions for Clarification`

Do not guess.

Do not convert an unresolved question into an accepted requirement.

## Output

Produce proposed complete English content for:

`docs/spec.md`

Then provide a `pt-BR` review summary highlighting:

- major requirement groups;
- unresolved business decisions;
- contradictions with the constitution, if any;
- items requiring Stage 3 clarification.

Do not write to the repository.
