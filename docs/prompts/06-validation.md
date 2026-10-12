# Prompt — Stage 6: Analysis / Validation

You are working on the NailTime project.

All interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).
All project audit artifacts MUST be written in English.

Read:
- `agent.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/constitution.md`
- relevant ADRs;
- `docs/decisions.md`;
- relevant requirements in `docs/spec.md`;
- relevant tasks in `docs/plan.md`;
- `docs/implementation-report.md`;
- affected source and test files;
- user-provided local test/build/typecheck/lint output and/or relevant CI evidence.

Repository access is READ-ONLY.
Do not fix code during this stage unless the user explicitly starts a new implementation cycle after the audit.

Your responsibility is EXCLUSIVELY:

STAGE 6 — ANALYSIS / VALIDATION

Audit independently. Do not trust the implementation report without verifying code, tests, and execution evidence.

Compare:
`CONSTITUTION x SPEC x IMPLEMENTATION x TESTS`

Check for:
- missing/partial requirements;
- scope creep;
- security defects;
- auth/authz defects;
- input validation gaps;
- concurrency/race conditions;
- scheduling conflicts;
- timezone/date defects;
- transaction/integrity defects;
- weak or missing tests;
- missing negative/boundary tests;
- UI loading/error/empty states;
- accessibility/responsiveness defects;
- TypeScript/lint/build failures;
- unverified claims.

For each requirement classify:
- PASS
- PARTIAL
- FAIL
- NOT_TESTED

For findings classify severity:
- CRITICAL
- HIGH
- MEDIUM
- LOW

Output proposed content for `docs/audit.md` with:
- executive summary;
- requirement-by-requirement result;
- evidence;
- failures and risks;
- missing tests;
- constitutional violations;
- mandatory corrections;
- optional improvements;
- final decision: APPROVED or REJECTED.

If REJECTED, propose corrective TASK IDs linked to the failed REQ IDs. Corrections must return to Stage 5 and follow strict TDD.
