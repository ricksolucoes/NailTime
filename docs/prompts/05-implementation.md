# G4DNailTime — Stage 5: Implementation with Strict TDD

## Responsibility

Perform EXCLUSIVELY:

`STAGE 5 — IMPLEMENTATION OF THE CURRENT TASK`

## Inputs

Read:
- governing policies;
- operational memory;
- Constitution;
- relevant ADRs/decisions;
- only relevant REQs;
- only current TASK/dependencies;
- directly affected source/tests.

Do not implement future tasks.

Do not invent requirements.

Do not silently change architecture.

## Pre-Implementation

Determine:
- current TASK;
- related REQs;
- acceptance criteria;
- dependencies;
- current TDD gate;
- relevant files;
- last verified evidence.

Explain this to user in `pt-BR`.

## Strict TDD

### RED

1. inspect code/tests;
2. determine whether valid RED already exists;
3. if not, produce smallest meaningful behavioral test;
4. return TEST-ONLY patch;
5. give exact command;
6. state expected behavioral failure;
7. STOP for execution evidence.

### GREEN

Only after valid RED:
1. return minimum production patch;
2. avoid speculative behavior;
3. give focused/regression commands;
4. STOP for GREEN evidence.

### REFACTOR

Only after GREEN:
1. identify useful structural improvements;
2. return separately when practical;
3. preserve behavior;
4. require rerun.

## Autonomous Behavior

Do not stop for routine technical decisions when authoritative artifacts and current documentation are sufficient.

If the available environment allows safe local execution without repository mutation, use it to inspect/validate as appropriate.

However, user/CI evidence remains required when the project policy or local environment cannot provide authoritative execution evidence.

## Critical Self-Review

Before each patch:
- verify minimality;
- verify no scope creep;
- check security;
- check concurrency/data integrity;
- check error handling;
- check test quality;
- check for simpler implementation;
- check compatibility with current docs.

Record non-scope improvements in improvement backlog.

## Output

For every proposal explain in `pt-BR`:
- ADD/MODIFY/DELETE;
- path;
- REQ/TASK/TEST;
- purpose;
- commands;
- expected result;
- evidence to return.

Code/tests/artifacts remain English.

At verified checkpoints propose updates to:
- `docs/implementation-report.md`
- `docs/assistant/session-state.md`
- memory files
- next handoff.

Do not write to GitHub.
