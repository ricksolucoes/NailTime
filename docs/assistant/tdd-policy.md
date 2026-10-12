# Strict TDD Policy

## Status

`MANDATORY`

## Core Rule

No new production behavior may be produced before a failing behavioral test exists and valid RED evidence is verified.

Sequence:

`REQ -> TASK -> TEST -> RED -> GREEN -> REFACTOR -> AUDIT`

## RED

1. Read relevant REQ and TASK.
2. Inspect existing code/tests.
3. Determine whether adequate valid RED already exists.
4. If not, design smallest meaningful behavioral test.
5. Return TEST-ONLY change.
6. Explain command and expected failure in `pt-BR`.
7. STOP before production implementation.

Valid RED:
- test discovered/executed;
- failure caused by missing/incorrect target behavior.

Invalid RED:
- syntax error;
- malformed test;
- setup failure;
- missing unrelated dependency;
- infrastructure failure;
- unrelated failure.

## GREEN

Only after valid RED:
1. return minimum production change;
2. avoid speculative behavior;
3. give focused/regression commands in `pt-BR`;
4. request execution evidence;
5. STOP before refactor.

## REFACTOR

Only after valid GREEN:
1. improve structure without new behavior;
2. return refactor separately when practical;
3. rerun relevant tests.

## Bugs

Bug fixes begin with a regression test that:
- fails before fix;
- fails for expected bug;
- passes after fix.

## Existing Failing Test

An existing failing test may satisfy RED if it expresses the exact desired behavior and fails for the expected reason.

## Non-Behavioral Changes

Documentation/formatting/mechanical changes may not require behavioral TDD.

Explain why in `pt-BR`.

## Evidence Record

Record:
- TEST ID;
- RED command/result;
- GREEN command/result;
- regression evidence;
- refactor verification;
- evidence source.
