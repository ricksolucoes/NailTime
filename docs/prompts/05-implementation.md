# G4DNailTime — Stage 5: Implementation with Strict TDD

Read first:

- `agent.md`
- `docs/prompts/_common.md`
- `docs/assistant/project-identity.md`
- `docs/assistant/language-policy.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/external-tools-policy.md`
- `docs/assistant/tdd-policy.md`
- `docs/assistant/context-recovery.md`
- `docs/assistant/session-state.md`
- `docs/constitution.md`
- relevant accepted ADRs and decisions
- only relevant requirement sections from `docs/spec.md`
- only the current task and required dependencies from `docs/plan.md`
- directly affected production and test files

Your responsibility in this conversation is EXCLUSIVELY:

`STAGE 5 — IMPLEMENTATION OF THE CURRENT TASK`

Do not implement future tasks.

Do not invent requirements.

Do not silently change architecture.

Do not write to the repository.

## Pre-Implementation Check

Before proposing any code, identify to the user in `pt-BR`:

- current TASK ID;
- related REQ IDs;
- acceptance criteria;
- relevant dependencies;
- current TDD gate;
- files inspected.

If required information is missing, ask only for information that cannot be obtained from the read-only repository or accepted artifacts.

## Mandatory TDD Gate

For new behavior or bug fixes, NEVER provide the production implementation in the same step as a new behavioral test.

### RED

1. Inspect current implementation and tests.
2. Determine whether valid RED already exists.
3. If not, design the smallest meaningful behavioral test.
4. Return only the test patch/file content.
5. Keep the project artifact content in English.
6. Explain application/testing steps to the user in `pt-BR`.
7. Provide the exact local command when known.
8. State the expected failure reason in `pt-BR`.
9. STOP.

Wait for user-provided execution evidence.

Only accept RED when the test executes and fails because the required behavior is missing or incorrect.

Syntax, setup, infrastructure, missing unrelated dependency, malformed fixture, or unrelated failures are not valid RED.

### GREEN

After valid RED evidence:

1. return the minimum production code patch required to satisfy the test;
2. do not add speculative behavior;
3. explain focused and regression commands to the user in `pt-BR`;
4. request execution evidence;
5. STOP.

Do not refactor before GREEN evidence exists.

### REFACTOR

After valid GREEN evidence:

1. identify optional structural improvements;
2. return refactor separately when practical;
3. preserve behavior;
4. require relevant tests to be rerun;
5. do not introduce new behavior.

## Current Documentation

For APIs that may have changed, consult current official documentation/Context7 using only generic technical queries.

Never send project code or repository content to Context7 or other external services.

## Delivery Format

For every proposal, explain in `pt-BR`:

- change type: ADD / MODIFY / DELETE;
- exact path;
- REQ/TASK/TEST IDs;
- purpose;
- local command(s);
- expected result;
- evidence the user should return.

The code, tests, file contents, comments, and project artifacts remain in English.

## Verified Checkpoint

Only after execution evidence supports the checkpoint, propose English updates to:

- `docs/implementation-report.md`;
- `docs/assistant/session-state.md`.

Do not claim completion without user or CI execution evidence.
