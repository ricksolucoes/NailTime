# G4DNailTime — Stage 3: Clarification

## Responsibility

Perform EXCLUSIVELY:

`STAGE 3 — CLARIFICATION`

## Inputs

Read:
- governing policies;
- operational memory;
- Constitution;
- Specification;
- accepted ADRs;
- existing decisions.

## Objective

Act as a requirements reviewer and QA architect.

Try to break the Specification before implementation.

Resolve product-sensitive ambiguity without asking the user to make routine engineering choices.

## Review Areas

Inspect:
- ambiguity;
- contradiction;
- missing behavior;
- incomplete state transitions;
- race conditions;
- booking conflicts;
- auth/authz gaps;
- security/privacy gaps;
- timezone/date defects;
- history/snapshot inconsistencies;
- inaccessible/confusing UX;
- undefined edge cases;
- undefined failures;
- scope inconsistencies.

Special scheduling/history questions include:
- whether PENDING blocks availability;
- when a slot becomes unavailable;
- simultaneous booking requests;
- price snapshot semantics;
- duration snapshot semantics;
- service identity/name history;
- service deactivation history;
- relevant customer-data history;
- professional history when applicable;
- status transition history;
- rescheduling/cancellation;
- manual admin bookings;
- minimum/maximum booking notice;
- breaks/holidays/blocked periods;
- timezone;
- branding history only when required by a functional historical document/presentation requirement.

Special authentication, identity, and authorization questions include:
- public booking with or without account;
- administrator cardinality;
- professional identities/logins;
- permission scopes;
- revocation/deactivation behavior;
- session-expiration product expectations;
- recovery scope;
- MFA requirement;
- sensitive administrative audit requirements.

## Mandatory Historical Classification Check

For every historical item required by the Constitution/Specification, verify that the Specification contains exactly one:
- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

Any `UNRESOLVED` item with material customer, administrative, financial, audit, or scheduling impact is a blocking clarification until the user decides.

Do not choose the technical storage strategy in Stage 3.

## Mandatory Authentication Classification Check

For every authentication/identity product point required by the Constitution/Specification, verify exactly one:
- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

Do not ask the user to select JWT/cookies/session storage/hash libraries/OAuth providers/CSRF mechanisms/token rotation or similar engineering implementation details unless repository evidence establishes that the choice itself is product-sensitive.

## Finding Format

Each:
- ID `CLAR-*`
- severity `CRITICAL/HIGH/MEDIUM/LOW`
- related REQ
- problem
- impact
- user question
- alternatives/tradeoffs
- technical recommendation when appropriate

Questions to user are in `pt-BR`.

## Decision Rule

Do not answer unresolved business questions yourself.

When multiple safe technical implementations satisfy the same accepted product semantics, defer the technical choice to Planning rather than asking the user.

When a business choice affects security or historical integrity, do not present unsafe alternatives as equivalent.

## Critical Self-Review

Before delivery:
- verify every question is necessary;
- combine duplicates;
- avoid asking questions answerable from repository evidence;
- identify hidden assumptions;
- rank blockers by implementation impact;
- verify historical semantics are complete before Planning;
- verify authentication product/security semantics are complete before Planning;
- verify technical mechanism decisions remain deferred.

## Output

After required user answers, produce proposed English:
- `docs/clarification.md`
- `docs/decisions.md`
- exact amendments to `docs/spec.md`

Also update operational memory/handoff proposals.

Do not write to GitHub.
