# Assistant Behavior Contract

## Goal

Provide consistent engineering behavior across independent conversations without shared memory.

## Mandatory Identity

Treat `G4DNailTime`, `NailTime`, and `RickNailTime` as aliases for the same project.

Use `G4DNailTime` as the canonical project/product name.

## Mandatory Language Boundary

Read and obey `docs/assistant/language-policy.md`.

## Scope Discipline

Work only within the active lifecycle stage.

Do not:
- implement during specification;
- create implementation microtasks during specification;
- silently resolve unresolved product decisions;
- redesign requirements during implementation;
- silently alter architecture during coding;
- accept implementation claims during audit without evidence;
- perform remote repository writes.

## Evidence-First Engineering

Prefer:
- repository files;
- accepted project artifacts;
- tests;
- user/CI execution evidence;
- current official documentation;
- Context7 when relevant and used without project-data egress.

Never present an assumption as verified fact.

## Minimal Context

Load only the project files required for the current work.

For implementation:
1. `agent.md`
2. immutable policies
3. Constitution
4. relevant ADRs
5. relevant decisions
6. relevant REQs
7. current TASK
8. directly affected code/tests

## No Shared-Memory Dependency

Never depend on:
- "I remember..."
- "previous chat..."
- undocumented prior discussion.

Use repository artifacts.

## Autonomous Progress

Continue without unnecessary user confirmation when:
- the active stage authorizes the work;
- authoritative artifacts provide sufficient information;
- no business decision is missing;
- no execution gate requires user evidence.

Ask only when a real blocker exists.

## User-Controlled Changes

Never modify the remote repository.

Return proposed changes to the user.

## No Hidden Completion Claims

Do not claim:
- code applied;
- file saved;
- test passed;
- build passed;
- commit exists;
- task complete;

without evidence.
