# G4DNailTime — Autonomous Resume Entrypoint

Use this prompt when starting a new conversation or resuming after context exhaustion.

## Mission

Reconstruct the current project state from the repository and continue the correct lifecycle work without depending on prior chat memory or the original supervising conversation.

## Mandatory Startup

Read in this order:

1. `agent.md`
2. `docs/assistant/project-identity.md`
3. `docs/assistant/language-policy.md`
4. `docs/assistant/behavior.md`
5. `docs/assistant/repository-policy.md`
6. `docs/assistant/external-tools-policy.md`
7. `docs/assistant/autonomous-operation.md`
8. `docs/assistant/critical-review.md`
9. `docs/assistant/tdd-policy.md`
10. `docs/assistant/context-recovery.md`
11. `docs/assistant/session-state.md`
12. `docs/assistant/memory/current-context.md`
13. `docs/assistant/memory/continuity-log.md`
14. `docs/assistant/memory/improvement-backlog.md`
15. `docs/assistant/memory/next-handoff.md`
16. `docs/prompts/_common.md`

Then inspect repository root and lifecycle artifacts.

## Determine Current Stage

Infer the active lifecycle stage from authoritative artifacts:

1. If `docs/constitution.md` is absent or not accepted:
   - use Stage 1.

2. If Constitution exists but `docs/spec.md` is absent/incomplete:
   - use Stage 2.

3. If Specification exists but unresolved clarification remains:
   - use Stage 3.

4. If clarification/decisions are resolved but `docs/plan.md` is absent/incomplete:
   - use Stage 4.

5. If plan contains incomplete implementation tasks:
   - use Stage 5 for the next permitted TASK.

6. If an implementation scope is complete and ready for independent audit:
   - use Stage 6.

Operational memory may help locate the current scope but cannot override normative artifacts.

## Stage Loading

After determining the stage, read the corresponding prompt:

- Stage 1: `docs/prompts/01-constitution.md`
- Stage 2: `docs/prompts/02-specification.md`
- Stage 3: `docs/prompts/03-clarification.md`
- Stage 4: `docs/prompts/04-planning.md`
- Stage 5: `docs/prompts/05-implementation.md`
- Stage 6: `docs/prompts/06-validation.md`

Then continue according to that stage.

## Autonomous Requirement

Do not ask the user which stage to run if the repository state makes it determinable.

Do not ask the user to restate prior context that exists in the repository.

Ask only for real blockers.

## Critical Review

Before continuing:
- detect contradictions;
- verify stale memory against normative files;
- identify missing artifacts;
- identify unsafe/inconsistent next actions.

## Output to User

In `pt-BR`, briefly report:

- detected lifecycle stage;
- current scope;
- active REQ/TASK/TEST if any;
- repository state used;
- blockers;
- next action.

Then continue the active stage autonomously.

## Continuity

At each stable checkpoint, propose updated operational memory and next handoff files so another conversation can continue.
