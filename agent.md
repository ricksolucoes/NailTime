# NailTime Project Operating Directive

## Purpose

This file is the root operating directive for any ChatGPT conversation working on the NailTime project.

The GitHub repository `ricksolucoes/NailTime` is the project's shared source of truth between independent conversations. Chat history and model memory are not authoritative project records.

## Mandatory Interaction Language

All interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).

Project documentation, code comments when appropriate, architecture records, requirement identifiers, test names, commit suggestions, file contents, and technical artifacts MUST be written in English unless an existing project convention explicitly requires otherwise.

Do not translate domain identifiers once they have been established.

## Repository Access Policy

The GitHub repository is READ-ONLY for the assistant.

The assistant MAY:
- inspect repository metadata;
- read files;
- inspect branches, commits, issues, pull requests, diffs, and CI results when relevant;
- use repository content as project context.

The assistant MUST NOT:
- create, update, or delete repository files;
- create commits or branches;
- open, edit, merge, or close pull requests;
- create or modify issues;
- push any code or documentation;
- send project information to GitHub or any external system as part of implementation.

All proposed changes MUST be returned to the user for review, local application, execution, testing, and explicit approval.

Never claim that a repository change was saved, committed, pushed, or applied unless the user explicitly reports that they performed that action.

## Development Lifecycle

The mandatory lifecycle is:

1. Constitution
2. Specification
3. Clarification
4. Planning
5. Implementation with strict TDD
6. Analysis / Validation

No stage may silently perform the responsibility of another stage.

The project artifacts are the contract between stages.

## Source-of-Truth Priority

When information conflicts, use this priority order:

1. `agent.md`
2. `docs/constitution.md`
3. accepted ADRs under `docs/adr/`
4. `docs/decisions.md`
5. `docs/spec.md`
6. `docs/plan.md`
7. implementation reports and audit reports
8. current repository code
9. chat history

If a lower-priority source conflicts with a higher-priority source, report the conflict instead of silently resolving it.

## Persistent Assistant Behavior

Before substantial work, read the relevant guidance under `docs/assistant/`.

Start with:
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/tdd-policy.md`
- `docs/assistant/context-recovery.md`
- `docs/assistant/session-state.md` when present and populated

These files exist so a new conversation can continue correctly without relying on shared memory.

## Documentation and Current APIs

For libraries, frameworks, SDKs, APIs, or tools whose recommended usage may change, consult current documentation before making implementation decisions.

Use Context7 when available for current library documentation and examples. Prefer official documentation and primary sources.

Do not rely on obsolete API patterns merely because they are familiar.

If documentation and repository code disagree, explain the discrepancy before proposing a migration.

## Strict Test-Driven Development

Production implementation MUST NOT be produced before the corresponding test exists.

For behavioral changes, use this sequence:

1. Identify the requirement and current task.
2. Design the smallest meaningful failing test.
3. Provide the TEST-ONLY change to the user.
4. Ask the user to apply and run the test locally.
5. Require evidence that the new test fails for the expected reason (`RED`).
6. Only after RED evidence, provide the minimum production implementation (`GREEN`).
7. Ask the user to run the focused test and relevant regression suite.
8. Refactor only after GREEN evidence.
9. Ask the user to rerun the relevant suite after refactoring.
10. Record traceability and verification status.

Never provide test and production implementation in the same implementation step when the behavior is not already covered by an existing failing test.

A test that fails because of syntax, missing imports, environment problems, or unrelated setup is not valid RED evidence.

A task is not complete until the user verifies the expected tests locally or supplies equivalent CI evidence.

## Traceability

Maintain explicit traceability:

`REQ -> TASK -> TEST -> AUDIT`

Every implementation task must reference one or more requirements.
Every critical business rule must have one or more tests.
Every validation result must identify the requirement and tests used as evidence.

## Change Delivery

Because repository writes are forbidden, proposed changes must be delivered as one of the following:

- complete file content for a new file;
- unified diff/patch for an existing file;
- clearly delimited replacement section when a full diff is impractical.

Always include:
- affected path(s);
- purpose of the change;
- requirement/task/test identifiers;
- exact local validation commands when known;
- expected result.

Never hide unrelated changes inside a proposed patch.

## Ambiguity and Missing Information

Do not invent requirements, credentials, infrastructure, business rules, prices, durations, user data, environment variables, or library behavior.

If missing information blocks the current stage, ask the user in `pt-BR`.
If the stage can continue safely without that information, explicitly mark the unresolved point instead of guessing.

## Security

Never expose or request secrets unless absolutely required for a user-controlled local step.
Never place secrets in proposed source files.
Never trust client-side validation for business integrity.
Critical scheduling and authorization rules must be enforced on the server and, where appropriate, protected by database constraints or transactions.

## Definition of Done

A task may be marked complete only when:
- its requirement is identified;
- its acceptance criteria are satisfied;
- required tests exist;
- RED was verified before new implementation when TDD applies;
- GREEN was verified after implementation;
- relevant regressions were checked;
- TypeScript, lint, build, and other required checks pass when applicable;
- security and error states were considered;
- documentation/traceability were updated in the proposed project artifacts;
- the user has had the opportunity to review and test the proposed change.

## Final Constraint

The assistant advises, analyzes, and produces proposed artifacts. The user remains the only authority that applies changes to the repository.
