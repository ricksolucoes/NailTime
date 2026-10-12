# Incremental Repository Synchronization Policy

## Purpose

Keep project context synchronized with GitHub without repeatedly loading the entire repository.

## Core Principle

Synchronization is SHA-based and incremental.

The assistant tracks:

- last verified branch;
- last verified commit SHA;
- current HEAD SHA;
- synchronization mode;
- relevant changed files;
- active-scope impact.

## Reserved Command

The exact user phrase:

`Atualizei o GitHub do NailTime.`

means:

`Synchronize from the last verified SHA to the current HEAD.`

## Algorithm

### 1. Read Current Snapshot

Read:
- default/current branch;
- current HEAD SHA.

### 2. Read Previous Snapshot

Read last verified branch/SHA from:
- `docs/assistant/session-state.md`;
- `docs/assistant/memory/current-context.md`.

### 3. Select Synchronization Mode

#### NO_CHANGE

Condition:

`CURRENT_HEAD == LAST_VERIFIED_SHA`

Action:
- no file reload unless separately required by active work.

#### INCREMENTAL

Condition:
- previous SHA exists;
- comparison is valid.

Action:
- inspect `LAST_VERIFIED_SHA..CURRENT_HEAD`;
- enumerate changed/added/deleted/renamed files;
- classify impact;
- reload only changed and directly impacted context.

#### BASELINE

Condition:
- no verified SHA exists.

Action:
- establish minimal project baseline;
- inspect structure/governance/memory/lifecycle state;
- avoid full repository ingestion.

#### FULL_RECOVERY

Condition:
- incremental comparison cannot be trusted.

Examples:
- rewritten history;
- missing old SHA;
- unexpected branch switch;
- large structural reorganization;
- contradictory state files;
- governing changes invalidate prior assumptions.

Action:
- perform structured recovery by relevance, not indiscriminate full loading.

## Impact Classification

### GOVERNANCE

Paths:
- `agent.md`
- `docs/assistant/*`
- `docs/prompts/*`

Reload changed governance files first.

### REQUIREMENTS

Paths:
- `docs/constitution.md`
- `docs/spec.md`
- `docs/clarification.md`
- `docs/decisions.md`
- `docs/adr/*`

Reload the changed artifact and affected downstream context as needed.

### PLANNING

Paths:
- `docs/plan.md`

Reload affected TASKs/dependencies.

### IMPLEMENTATION

Paths:
- source;
- tests;
- migrations;
- configuration;
- schemas.

Reload changed files and direct dependencies/dependents necessary for the active scope.

### OPERATIONAL_MEMORY

Paths:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/*`

Reload changed continuation state.

### UNRELATED

Record that the file changed but do not pollute active context.

## Dependency Expansion

A changed implementation file does not automatically require loading an entire module/repository.

Expand context only when needed through:
- imports;
- direct callers;
- direct consumers;
- associated tests;
- schemas/types/contracts;
- migrations;
- related task/requirement.

## Governance Change Escalation

If `agent.md` or a fundamental assistant policy changes:

1. reload the changed governance file immediately;
2. re-evaluate synchronization rules;
3. expand reload scope only when the new rule requires it.

## Memory Update

After successful synchronization, propose updates containing:

- previous verified SHA;
- current verified SHA;
- branch;
- synchronization mode;
- changed files/areas;
- relevant files reloaded;
- unrelated changes ignored;
- active-stage impact;
- next action.

## Safety

Synchronization is read-only.

Never mutate GitHub.
