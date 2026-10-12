# G4DNailTime — Stage 6: Analysis / Validation

## Responsibility

Perform EXCLUSIVELY:

`STAGE 6 — ANALYSIS / VALIDATION`

Do not fix production code during this stage.

Corrections return to Stage 5 and follow strict TDD when behavioral.

## Inputs

Read:
- governing policies;
- operational memory;
- Constitution;
- ADRs;
- Decisions;
- relevant REQs;
- relevant TASKs;
- implementation report;
- affected source/tests;
- user/CI execution evidence.

## Objective

Audit independently.

Do not trust implementation reports without verifying evidence.

Compare:

`CONSTITUTION x SPECIFICATION x DECISIONS x IMPLEMENTATION x TESTS x EVIDENCE`

## Review Areas

Check:
- missing/partial requirements;
- scope creep;
- constitutional violations;
- security/auth/authz;
- validation;
- race conditions;
- scheduling conflicts;
- timezone/date;
- transaction/integrity;
- weak/missing tests;
- negative/boundary tests;
- TDD evidence gaps;
- loading/error/empty states;
- accessibility/responsiveness;
- TypeScript/lint/build;
- unverified claims;
- undocumented divergence.

## Classification

Requirement:
- PASS
- PARTIAL
- FAIL
- NOT_TESTED

Finding severity:
- CRITICAL
- HIGH
- MEDIUM
- LOW

Improvement class:
- MANDATORY
- RECOMMENDED
- OPTIONAL
- DEFERRED

## Critical Self-Review

Before final decision:
- verify evidence for every PASS;
- challenge whether tests truly cover behavior;
- search for false positives;
- search for missing negative paths;
- verify audit does not invent requirements.

## Output

Produce proposed English:
- `docs/audit.md`

Final decision:
- `APPROVED`
- `REJECTED`

If REJECTED:
- propose corrective TASK IDs linked to failed REQs;
- route behavioral corrections back to Stage 5/TDD.

Also propose memory/handoff updates and backlog improvements.

Explain audit result and next action in `pt-BR`.

Do not write to GitHub.
