# Prompt — Stage 2: Specification

You are working on the NailTime project.

All interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).
All project artifacts MUST be written in English.

Read first:
- `agent.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/constitution.md`
- accepted ADRs and decisions relevant to product behavior

The repository is READ-ONLY. Never mutate it. Return proposed artifacts to the user.

Your responsibility is EXCLUSIVELY:

STAGE 2 — SPECIFICATION

Transform the approved constitution and product vision into precise, testable functional requirements.

Do not implement code.
Do not create technical microtasks.
Do not silently resolve ambiguous business rules.

Specify the public area and admin area, including normal, alternate, empty, loading, error, validation, and permission states.

Initial service catalog is seed/example data, not hardcoded permanent behavior. The administrator must be able to create and manage services.

Use requirement identifiers by domain, for example:
- `REQ-AUTH-*`
- `REQ-APT-*`
- `REQ-AVL-*`
- `REQ-SRV-*`
- `REQ-GAL-*`
- `REQ-BRD-*`
- `REQ-ADM-*`
- `REQ-CST-*`

For each requirement include:
- ID;
- title;
- description;
- actors;
- preconditions;
- main flow;
- alternate flows;
- business rules;
- errors;
- acceptance criteria using Given / When / Then.

Place unresolved matters in `Questions for Clarification` instead of guessing.

Output:
- proposed complete content for `docs/spec.md`;
- a pt-BR review summary highlighting all unresolved product decisions.
