# Strict TDD Policy

## Core Rule

No new production behavior before a failing test that specifies that behavior.

The implementation conversation uses a gated RED -> GREEN -> REFACTOR workflow.

## Phase A — RED

1. Read the relevant requirement and task.
2. Inspect existing tests and implementation.
3. Determine whether an existing test already fails for the required behavior.
4. If not, design the smallest meaningful test.
5. Deliver only the test change.
6. Provide the exact command the user should run.
7. State the expected failure reason.
8. Stop before production implementation.

The user applies the test and returns the result.

Valid RED evidence means:
- the new test executes;
- it fails;
- the failure is caused by missing/incorrect target behavior.

Invalid RED evidence includes:
- syntax failure;
- missing dependency;
- unresolved import unrelated to target behavior;
- broken fixture/setup;
- infrastructure failure;
- unrelated existing failure.

## Phase B — GREEN

Only after valid RED evidence:
1. provide the minimum production change required to make the test pass;
2. do not add speculative behavior;
3. provide focused and regression test commands;
4. ask the user to run them;
5. stop before refactoring until GREEN evidence exists.

## Phase C — REFACTOR

Only after GREEN evidence:
1. identify optional structural improvements;
2. preserve behavior;
3. provide refactor patch separately;
4. require the relevant tests to be rerun.

## Existing Bugs

A bug fix must begin with a regression test reproducing the bug.
The regression test must fail before the fix and pass after the fix.

## Non-Behavioral Changes

Pure documentation, formatting, mechanical rename, or configuration-only work may not require RED/GREEN if no executable behavior changes.
State explicitly why TDD does not apply.

## Completion Evidence

Record:
- TEST identifier;
- RED command and observed result;
- GREEN command and observed result;
- regression checks;
- user/CI evidence source.

Do not mark a TDD task complete without execution evidence.
