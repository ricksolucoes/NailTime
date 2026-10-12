# G4DNailTime — Stage 6: Analysis / Validation

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- relevant files under `docs/assistant/`
- `docs/constitution.md`
- relevant accepted ADRs
- `docs/decisions.md`
- relevant requirements in `docs/spec.md`
- relevant tasks in `docs/plan.md`
- `docs/implementation-report.md`
- affected source and test files
- user-provided local test/build/typecheck/lint output and/or relevant CI evidence

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 6 — ANALYSIS / VALIDATION`

Do not fix production code during this stage.

Corrections must return to Stage 5 and follow strict TDD when behavior changes.

## Objective

Audit independently.

Do not trust the implementation report without verifying code, tests, accepted artifacts, and execution evidence.

Compare:

`CONSTITUTION x SPECIFICATION x IMPLEMENTATION x TESTS`

## Review Areas

Check for:

- missing requirements;
- partially implemented requirements;
- scope creep;
- constitutional violations;
- security defects;
- authentication defects;
- authorization defects;
- input-validation gaps;
- race conditions;
- scheduling conflicts;
- concurrency defects;
- timezone/date defects;
- transaction/integrity defects;
- weak tests;
- missing tests;
- missing negative/boundary tests;
- TDD evidence gaps;
- loading/error/empty-state defects;
- accessibility defects;
- responsiveness defects;
- TypeScript/lint/build failures;
- unverified claims;
- undocumented technical divergence.

## Requirement Classification

For each requirement classify:

- `PASS`
- `PARTIAL`
- `FAIL`
- `NOT_TESTED`

## Finding Severity

For each finding classify:

- `CRITICAL`
- `HIGH`
- `MEDIUM`
- `LOW`

## Evidence Rule

Every approval must identify evidence.

Do not accept statements such as:

- "the report says it works";
- "the developer says tests passed";
- "it should be fine".

Prefer:

- repository code;
- tests;
- user-provided execution output;
- CI evidence;
- accepted project artifacts.

## Output

Produce proposed English content for:

`docs/audit.md`

Include:

- executive summary;
- requirement-by-requirement result;
- evidence;
- failures and risks;
- missing tests;
- constitutional violations;
- mandatory corrections;
- optional improvements;
- final decision: `APPROVED` or `REJECTED`.

If `REJECTED`, propose corrective TASK IDs linked to failed REQ IDs.

Behavioral corrections must return to Stage 5 and follow strict TDD.

Then explain the audit result and next permitted action to the user in `pt-BR`.

Do not write to the repository.
