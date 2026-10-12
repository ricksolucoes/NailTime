# G4DNailTime — Autonomous Resume Entrypoint

Use this prompt when starting a new conversation or resuming after context exhaustion.

## Mission

Reconstruct the current project state from repository evidence and continue the correct lifecycle work without depending on prior chat memory.

## Step 1 — Load Minimal Governance

Read:

1. `agent.md`
2. `docs/assistant/repository-policy.md`
3. `docs/assistant/repository-sync.md`
4. `docs/assistant/session-state.md`
5. `docs/assistant/memory/current-context.md`
6. `docs/assistant/memory/next-handoff.md`
7. `docs/prompts/_common.md`

Load other assistant policies only when relevant to the detected work.

## Step 2 — Synchronize Repository Incrementally

Read:
- current default/current branch;
- current HEAD SHA;
- last verified branch/SHA from operational memory.

Select:

### NO_CHANGE
If current HEAD equals last verified SHA.

### INCREMENTAL
If previous SHA exists and a safe comparison is possible.

Inspect:

`LAST_VERIFIED_SHA..CURRENT_HEAD`

Then:
- enumerate changed files;
- classify impact;
- reload only changed and directly affected context.

### BASELINE
If no previous SHA is available.

Inspect only enough repository structure/governance/lifecycle state to establish the first verified snapshot.

### FULL_RECOVERY
Only when incremental comparison is unsafe/impossible.

Do not read the whole repository merely because a new conversation started.

## Step 3 — Determine Current Stage

Infer the active lifecycle stage from authoritative artifacts:

1. missing/unaccepted Constitution -> Stage 1;
2. Constitution exists, Specification missing/incomplete -> Stage 2;
3. unresolved clarification -> Stage 3;
4. clarified but plan missing/incomplete -> Stage 4;
5. incomplete planned implementation work -> Stage 5;
6. completed implementation scope ready for audit -> Stage 6.

Operational memory helps locate scope but cannot override normative artifacts.

## Step 4 — Load Active Stage

Read only the corresponding prompt:

- Stage 1: `docs/prompts/01-constitution.md`
- Stage 2: `docs/prompts/02-specification.md`
- Stage 3: `docs/prompts/03-clarification.md`
- Stage 4: `docs/prompts/04-planning.md`
- Stage 5: `docs/prompts/05-implementation.md`
- Stage 6: `docs/prompts/06-validation.md`

Then load only artifacts/code/tests required by that stage and active scope.

## Autonomous Requirement

Do not ask the user which stage to run when repository state makes it determinable.

Do not ask the user to restate repository information.

Ask only for real blockers.

## Critical Review

Before continuing:
- detect contradictions;
- validate operational memory against normative artifacts;
- identify missing artifacts;
- identify unsafe next actions;
- identify stale scope caused by the latest diff.

## Output to User

In `pt-BR`, briefly report:

- detected lifecycle stage;
- current scope;
- active REQ/TASK/TEST;
- previous verified SHA;
- current HEAD SHA;
- synchronization mode;
- materially changed areas;
- context actually reloaded;
- unrelated changes ignored;
- blockers;
- next action.

Then continue the active stage autonomously.

## Continuity

At stable checkpoints propose updated memory/handoff files with the newly verified SHA.
