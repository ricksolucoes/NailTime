# Strict TDD Policy

## Status

`MANDATORY`

## Core Rule

No new production behavior may be produced before a failing behavioral test exists and valid RED evidence has been verified.

The implementation lifecycle uses a gated:

`RED -> GREEN -> REFACTOR`

workflow.

## Traceability

Each behavior change must preserve:

`REQ -> TASK -> TEST -> AUDIT`

A test must identify the requirement/task behavior it protects.

## Phase A — RED

1. Read the relevant requirement and current task.
2. Inspect existing tests and implementation.
3. Determine whether an existing test already fails for the required behavior.
4. If no adequate failing test exists, design the smallest meaningful test.
5. Return only the test change to the user.
6. Explain the change and execution command in `pt-BR`.
7. State the expected behavioral failure reason in `pt-BR`.
8. STOP before production implementation.

The user applies the test and returns execution evidence.

### Valid RED

Valid RED evidence means:

- the test is discovered and executed;
- the test fails;
- the failure is caused by missing or incorrect target behavior;
- unrelated tests/environment are not the cause.

### Invalid RED

The following do not count as valid RED:

- syntax failure;
- compile failure caused by a malformed test;
- missing dependency unrelated to the behavior;
- unresolved import caused by test setup mistakes;
- broken fixture/setup;
- infrastructure failure;
- database/service unavailable for unrelated reasons;
- unrelated pre-existing failure.

When RED is invalid, fix only the test/setup problem required to obtain meaningful RED. Do not implement production behavior.

## Phase B — GREEN

Only after valid RED evidence:

1. return the minimum production change required to satisfy the failing test;
2. do not add speculative behavior;
3. explain focused and regression commands in `pt-BR`;
4. ask the user to run them;
5. STOP before refactoring until GREEN evidence exists.

### Valid GREEN

GREEN requires evidence that:

- the target test passes;
- relevant focused tests pass;
- relevant regression tests pass or any failures are explicitly analyzed;
- the implementation satisfies the intended requirement rather than merely bypassing the test.

## Phase C — REFACTOR

Only after valid GREEN evidence:

1. identify optional structural improvements;
2. preserve externally observable behavior;
3. return refactoring separately from the GREEN implementation when practical;
4. require relevant tests to be rerun;
5. do not introduce new behavior during refactoring.

## Bug Fixes

Every behavioral bug fix starts with a regression test reproducing the bug.

The regression test must:

1. fail before the fix;
2. fail for the expected bug;
3. pass after the fix.

## Existing Test Coverage

If an existing test already expresses the exact required behavior and currently fails for the expected reason, that evidence may satisfy the RED gate.

Do not add a duplicate test only to satisfy process ceremony.

## Non-Behavioral Changes

Pure documentation, formatting, comments, mechanical rename, or configuration-only work may not require RED/GREEN when no executable behavior changes.

The assistant must explain to the user in `pt-BR` why strict behavioral TDD does not apply.

## Completion Evidence

Record in the proposed implementation report:

- TEST identifier;
- RED command;
- RED observed result;
- RED evidence source;
- GREEN command;
- GREEN observed result;
- regression commands/results;
- refactor verification when applicable;
- user/CI evidence source.

Do not mark a TDD task complete without execution evidence.
