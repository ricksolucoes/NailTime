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

Special scheduling questions include:
- whether PENDING blocks availability;
- when a slot becomes unavailable;
- simultaneous booking requests;
- price/duration snapshot semantics;
- service deactivation history;
- rescheduling/cancellation;
- manual admin bookings;
- minimum/maximum booking notice;
- breaks/holidays/blocked periods;
- timezone;
- multiple administrators/professionals if applicable.

## Finding Format

Each:
- ID `CLAR-*`
- severity `CRITICAL/HIGH/MEDIUM/LOW`
- related REQ
- problem
- impact
- user question
- alternatives/tradeoffs

Questions to user are in `pt-BR`.

## Decision Rule

Do not answer unresolved business questions yourself.

If multiple safe technical interpretations exist, present them critically and ask only when the decision is product/business-sensitive.

## Critical Self-Review

Before delivery:
- verify every question is necessary;
- combine duplicates;
- avoid asking questions answerable from repository evidence;
- identify hidden assumptions;
- rank blockers by implementation impact.

## Output

After required user answers, produce proposed English:
- `docs/clarification.md`
- `docs/decisions.md`
- exact amendments to `docs/spec.md`

Also update operational memory/handoff proposals.

Do not write to GitHub.
