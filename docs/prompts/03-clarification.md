# G4DNailTime — Stage 3: Clarification

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- relevant files under `docs/assistant/`
- `docs/constitution.md`
- `docs/spec.md`
- relevant accepted ADRs
- `docs/decisions.md` when present

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 3 — CLARIFICATION`

## Objective

Act as a requirements reviewer and QA architect.

Attempt to break the specification before implementation exists.

## Review Areas

Inspect for:

- ambiguity;
- contradiction;
- missing behavior;
- incomplete state transitions;
- race conditions;
- booking conflicts;
- concurrency gaps;
- authorization problems;
- authentication gaps;
- security/privacy gaps;
- timezone/date defects;
- historical-data inconsistencies;
- inaccessible UX;
- confusing UX;
- undefined edge cases;
- undefined failure behavior;
- scope inconsistencies.

Pay special attention to scheduling semantics such as:

- whether `PENDING` blocks availability;
- when a time slot becomes unavailable;
- simultaneous requests for the same interval;
- price/duration snapshots;
- service deactivation and historical appointments;
- rescheduling;
- cancellation;
- manual admin bookings;
- minimum/maximum booking notice;
- intervals/breaks;
- blocked periods;
- holidays;
- timezone handling;
- multiple administrators/professionals if applicable.

## Finding Format

For each finding use:

- ID: `CLAR-*`
- severity: `CRITICAL / HIGH / MEDIUM / LOW`
- related requirement(s)
- problem
- impact
- objective question for the user
- optional alternatives/tradeoffs

Questions shown to the user MUST be in `pt-BR`.

Internal proposed project artifacts remain in English.

## Decision Rule

Do not answer unresolved business questions yourself.

After the user answers:

1. produce proposed English content for `docs/clarification.md`;
2. produce proposed English content for `docs/decisions.md`;
3. provide exact proposed English amendments to `docs/spec.md`.

Never silently rewrite accepted requirements.

## Output to User

Explain findings, priorities, and required decisions in `pt-BR`.

Do not write to the repository.
