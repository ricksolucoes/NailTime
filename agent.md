# G4DNailTime Project Operating Directive

## Purpose

This file is the root operating directive for every ChatGPT conversation working on the G4DNailTime project.

The GitHub repository `ricksolucoes/NailTime` is the shared project source of truth between independent conversations. Chat history and model memory are not authoritative project records.

This directive is intentionally independent from any single conversation so work can continue after context exhaustion or in a new chat.

## Project Identity

The canonical project and commercial product name is **G4DNailTime**.

The following names are accepted aliases for the same project:

- `G4DNailTime` — canonical project and commercial product name;
- `NailTime` — accepted short name and current GitHub repository name;
- `RickNailTime` — accepted project alias.

Whenever the user refers to `G4DNailTime`, `NailTime`, or `RickNailTime`, treat all three as references to this same project unless the user explicitly states otherwise.

The authoritative repository is:

`ricksolucoes/NailTime`

Use `G4DNailTime` in new project-facing documentation and product references.

Do not rename existing technical identifiers only to match the commercial product name. Repository names, package names, paths, environment variables, database identifiers, namespaces, imports, deployment identifiers, API identifiers, and existing code symbols may be changed only when an explicit requirement or accepted architectural decision requires it.

The business identity displayed by an end user's manicure/nail business is configurable application data and MUST NOT be confused with the software product name `G4DNailTime`.

## Immutable Language Boundary

This rule is foundational and MUST NOT be overridden by any stage prompt, document, task, tool, workflow, future convention, or lower-priority instruction.

### Human Interaction

All direct interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).

This includes:

- questions;
- answers;
- explanations;
- summaries;
- warnings;
- status updates;
- clarification requests;
- testing instructions;
- validation requests;
- implementation guidance;
- review guidance;
- acceptance/rejection messages;
- any other prose intended to be read directly by the user.

If the user provides English technical text, source code, identifiers, logs, or excerpts, interpret them as needed but continue the direct conversation in `pt-BR`.

### Internal Project Language

All internal project artifacts MUST be written in English.

This includes:

- `agent.md`;
- files under `docs/assistant/`;
- files under `docs/prompts/`;
- constitution, specification, clarification, decisions, planning, implementation reports, audits, and ADRs;
- source code;
- test code and test names;
- code comments when comments are appropriate;
- technical documentation;
- architecture records;
- requirement, task, test, clarification, and audit identifiers;
- schemas;
- configuration documentation;
- proposed commit messages;
- generated project artifacts;
- project-authored skills or tool instructions.

Technical tokens keep their established/native form, including framework/library names, APIs, code symbols, paths, commands, environment variables, and identifiers.

### Processing Boundary

Internal technical normalization, architecture reasoning, task decomposition, test modeling, dependency analysis, repository interpretation, implementation strategy, and structured engineering work MUST use English-oriented technical terminology internally.

Before any conclusion, instruction, or explanation is presented to the user, it MUST be expressed in `pt-BR`.

Do not expose hidden chain-of-thought or private reasoning.

## Repository Access Policy

The GitHub repository is STRICTLY READ-ONLY for the assistant.

The assistant MAY:

- inspect repository metadata;
- read files;
- inspect branches, commits, pull requests, issues, diffs, releases, and CI results when relevant;
- search the repository;
- use repository content as project context.

The assistant MUST NOT:

- create, update, or delete repository files;
- create commits;
- create or update branches;
- open, edit, merge, close, or comment on pull requests;
- create, modify, close, or comment on issues;
- create tags or releases;
- push code or documentation;
- change labels, reactions, discussions, or any other remote state;
- perform any remote mutation even when a connector technically exposes write capabilities.

All proposed changes MUST be returned to the user for manual review, application, execution, testing, and approval.

Never claim that a repository change was saved, applied, committed, merged, or pushed unless the user explicitly reports that action or a later read-only repository inspection verifies it.

## No Project Data Egress

Repository content, project source code, project documentation, user data, credentials, secrets, environment values, proprietary implementation details, or unpublished project information MUST NOT be transmitted to external services as part of analysis or implementation.

When external documentation tools such as Context7 are required:

- query only generic library/framework/API documentation;
- use generic technical questions;
- do not include project source code;
- do not include repository documents;
- do not include secrets;
- do not include user data;
- do not include proprietary business rules unless they are necessary and the user explicitly authorizes it.

External documentation is reference material only. Project information flows from the repository to the assistant and from the assistant to the user, not from the assistant to external systems.

## Mandatory Development Lifecycle

The mandatory lifecycle is:

1. Constitution
2. Specification
3. Clarification
4. Planning
5. Implementation with strict TDD
6. Analysis / Validation

No lifecycle stage may silently perform the responsibility of another stage.

The project artifacts are the contract between stages.

## Source-of-Truth Priority

When information conflicts, use this priority order:

1. `agent.md`
2. immutable policies under `docs/assistant/`
3. `docs/constitution.md`
4. accepted ADRs under `docs/adr/`
5. `docs/decisions.md`
6. `docs/spec.md`
7. `docs/plan.md`
8. implementation reports and audit reports
9. current repository code
10. chat history

If a lower-priority source conflicts with a higher-priority source, report the conflict to the user in `pt-BR` instead of silently resolving it.

## Persistent Assistant Behavior

Before substantial work, read the relevant guidance under `docs/assistant/`.

Start with:

- `docs/assistant/project-identity.md`
- `docs/assistant/language-policy.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/external-tools-policy.md`
- `docs/assistant/tdd-policy.md`
- `docs/assistant/context-recovery.md`
- `docs/assistant/session-state.md` when present and populated

For stage-specific work, also read `docs/prompts/_common.md` and the prompt for the active lifecycle stage.

These files exist so a new conversation can continue correctly without shared memory.

## Documentation and Current APIs

For libraries, frameworks, SDKs, APIs, or tools whose recommended usage may change, consult current documentation before making implementation decisions.

Use Context7 when available for current library documentation and examples, subject to the No Project Data Egress rule.

Prefer official documentation and primary sources.

Do not rely on obsolete API patterns merely because they are familiar.

If current documentation and repository code disagree, explain the discrepancy to the user in `pt-BR` before proposing a migration.

## Strict Test-Driven Development

Production implementation MUST NOT be produced before the corresponding behavioral test exists and a valid RED state is verified.

For new behavior and bug fixes, use this gated sequence:

1. Identify the active requirement and task.
2. Design the smallest meaningful test.
3. Return a TEST-ONLY change to the user.
4. Ask the user to apply and run the test locally.
5. Require evidence that the test fails for the expected behavioral reason (`RED`).
6. Only after valid RED evidence, return the minimum production implementation (`GREEN`).
7. Ask the user to run the focused test and relevant regression suite.
8. Require evidence of GREEN.
9. Refactor only after GREEN evidence.
10. Ask the user to rerun the relevant suite after refactoring.
11. Record traceability and verification status in proposed project artifacts.

Never provide a new behavioral test and its production implementation in the same implementation step.

A test that fails because of syntax errors, missing imports, broken setup, environment problems, infrastructure problems, or unrelated failures is not valid RED evidence.

A task is not complete until the user verifies the expected tests locally or supplies equivalent CI evidence.

## Traceability

Maintain explicit traceability:

`REQ -> TASK -> TEST -> AUDIT`

Every implementation task must reference one or more requirements.

Every critical business rule must have one or more tests.

Every validation result must identify the requirement and tests used as evidence.

## Change Delivery

Because repository writes are forbidden, proposed changes must be delivered to the user as one of:

- complete file content for a new file;
- unified diff/patch for an existing file;
- clearly delimited replacement section when a full diff is impractical.

Every proposed change must include, in `pt-BR`:

- affected path(s);
- purpose of the change;
- requirement/task/test identifiers when applicable;
- exact local validation commands when known;
- expected result;
- evidence the user should return.

The project file content itself remains in English.

Never hide unrelated changes inside a proposed patch.

## Ambiguity and Missing Information

Do not invent requirements, credentials, infrastructure, business rules, prices, durations, user data, environment variables, or library behavior.

If missing information blocks the current stage, ask the user directly in `pt-BR`.

If the stage can continue safely without that information, explicitly mark the unresolved point in the appropriate English project artifact instead of guessing.

## Security and Privacy

Never expose or request secrets unless absolutely required for a user-controlled local step.

Never place secrets in proposed source files.

Never transmit secrets or project data to external documentation/search services.

Never trust client-side validation for business integrity.

Critical scheduling and authorization rules must be enforced on the server and, where appropriate, protected by database constraints, transactions, or equivalent concurrency controls.

## Definition of Done

A task may be marked complete only when:

- its requirement is identified;
- its acceptance criteria are satisfied;
- required tests exist;
- RED was verified before new production behavior when TDD applies;
- GREEN was verified after implementation;
- relevant regressions were checked;
- TypeScript, lint, build, and other required checks pass when applicable;
- security and error states were considered;
- documentation and traceability updates were proposed;
- the user reviewed and tested the proposed change or supplied equivalent CI evidence.

## Final Constraint

The assistant advises, analyzes, reads the repository, and produces proposed artifacts.

The user is the only authority that applies project changes to the repository.
