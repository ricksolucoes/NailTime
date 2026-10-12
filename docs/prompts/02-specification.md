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

Do not choose technical persistence/authentication mechanisms that belong to Planning.

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

## Mandatory Historical Snapshot Semantics

The Specification MUST explicitly evaluate mutable information referenced by an appointment.

At minimum evaluate:
- service name;
- price;
- duration;
- category or description when historically relevant;
- professional when that concept exists;
- date/time and timezone;
- relevant customer data;
- appointment status and status transitions;
- branding only if a functional requirement requires preserving the presentation that existed at that time.

For each item classify exactly one:
- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

Define business semantics only. Do NOT decide schema, denormalization, version tables, snapshot columns, event sourcing, or other persistence mechanics.

Price and duration MUST NOT remain accidentally ambiguous until Planning. The Specification must answer whether later service edits can change the meaning of an already-created appointment or explicitly mark the point `UNRESOLVED`.

If the choice affects customer-visible behavior, administrative history, financial meaning, audit meaning, or scheduling integrity:
- explain the decision in `pt-BR`;
- explain impacts of alternatives;
- provide a recommendation;
- ask the user only for the actual business decision.

Do not invent the answer.

## Mandatory Authentication / Identity Product Semantics

Before technical authentication design, the Specification MUST evaluate:
- who must authenticate;
- whether public booking requires a customer account;
- whether customers may book without registration;
- who may access administration;
- one vs multiple administrators;
- professionals and whether they have separate login;
- permission levels;
- actions requiring authentication;
- actions requiring specific authorization;
- incorrect-login behavior;
- abusive-attempt protection requirement;
- logout;
- session expiration semantics;
- password change;
- access recovery;
- access revocation;
- deactivated-user behavior;
- MFA requirement;
- minimum audit requirements for sensitive admin actions.

For each point classify exactly one:
- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

Do not ask the user to choose implementation mechanics such as JWT vs cookie, server-side sessions, OAuth/OIDC provider, hashing library, token format, session storage, email provider, CSRF mechanism, token rotation, or MFA technology unless a real business requirement makes that choice product-sensitive.

Security guarantees established by the Constitution remain mandatory even when implementation mechanics are deferred.

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

Ask only questions that materially require product/business authority.

## Critical Self-Review

Before delivery:
- search for contradictions;
- identify missing states;
- identify race/concurrency implications;
- verify every required historical-snapshot classification exists;
- verify price/duration semantics are resolved or explicitly escalated;
- verify authentication/identity product semantics are classified;
- check privacy/security implications;
- check whether acceptance criteria are executable/testable;
- identify unnecessary scope;
- verify no technical implementation choice was prematurely turned into a business requirement.

## Output

Produce proposed English content for:
- `docs/spec.md`

Also propose updated memory/handoff files.

Explain unresolved decisions and required review in `pt-BR`.

Do not write to GitHub.
