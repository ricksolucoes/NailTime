# G4DNailTime Project Operating Directive

## Purpose

This file is the root operating directive for every ChatGPT conversation working on the G4DNailTime project.

The authoritative GitHub repository is:

`ricksolucoes/NailTime`

The repository is the shared source of truth between independent conversations. Chat history and model memory are not authoritative project records.

This operating model is designed so a new conversation can resume work without depending on:
- a previous chat;
- shared model memory;
- the original supervising conversation;
- undocumented assumptions.

## Project Identity

Canonical project and commercial software product name:

`G4DNailTime`

Accepted aliases for the same project:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

Whenever the user uses any accepted alias, treat it as the same project unless the user explicitly states otherwise.

The repository name `NailTime` is a technical repository identifier and does not override the canonical product name.

Do not rename established technical identifiers merely to match the commercial product name unless an explicit requirement or accepted architectural decision requires it.

The branding displayed by a manicure/nail business using the software is configurable application data and MUST NOT be confused with the G4DNailTime software product identity.

## Immutable Language Boundary

This rule is foundational and MUST NOT be overridden by any prompt, lifecycle stage, task, document, tool, workflow, future convention, or lower-priority instruction.

### Human Interaction

All direct interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).

### Internal Project Language

All internal project artifacts MUST be written in English.

This includes:
- operating directives;
- assistant behavior files;
- lifecycle prompts;
- source code;
- tests and test names;
- technical comments;
- architecture records;
- requirements;
- decisions;
- plans;
- reports;
- audits;
- ADRs;
- operational memory files;
- project-authored skills and tool instructions.

Technical tokens preserve their established/native form.

### Processing Boundary

Internal engineering structures use English-oriented technical terminology.

All user-facing conclusions MUST be expressed in `pt-BR`.

Never expose private chain-of-thought or hidden reasoning.

## Repository Access Policy

GitHub access is STRICTLY READ-ONLY for the assistant.

Allowed:
- inspect repository metadata;
- read repository files;
- search code;
- inspect branches, commits, diffs, pull requests, issues, releases, and CI evidence.

Forbidden:
- create/update/delete remote files;
- commit or push;
- create/update branches;
- mutate pull requests/issues/releases;
- comment, label, react, merge, or perform any other remote write.

Connector write capability is not permission.

All repository changes are proposals until:
- the user manually applies them; or
- a later read-only inspection verifies them.

## Incremental Repository Synchronization

Repository synchronization MUST be incremental by default.

The assistant MUST track the last verified repository snapshot using:
- branch;
- commit SHA;
- verification mode;
- verification timestamp when available.

The main synchronization state is stored in:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`

### Reserved Refresh Command

The exact user phrase:

`Atualizei o GitHub do NailTime.`

is a reserved project control command.

It means:

`Synchronize the assistant's project state with every repository change since the last verified commit.`

It DOES NOT mean:

`Re-read the entire repository.`

### Mandatory Incremental Refresh Algorithm

When the refresh command is received:

1. invalidate assumptions about repository state after the last verified SHA;
2. read the current default branch and current `HEAD` SHA;
3. read the last verified branch/SHA from operational memory;
4. compare the current `HEAD` with the last verified SHA.

Then follow one of these modes:

#### Mode A — NO_CHANGE

Use when:

`CURRENT_HEAD == LAST_VERIFIED_SHA`

Actions:
- do not reload unchanged project files;
- report in `pt-BR` that no repository changes were detected;
- continue current work.

#### Mode B — INCREMENTAL

Use when:
- a previous verified SHA exists;
- the branch/history relationship can be safely compared;
- the previous snapshot is a valid base for the current repository state.

Actions:
1. inspect the commit/diff range:
   `LAST_VERIFIED_SHA..CURRENT_HEAD`;
2. identify changed/added/deleted/renamed files;
3. classify each change by impact;
4. reload only:
   - changed governing files;
   - changed lifecycle artifacts;
   - changed operational memory files;
   - changed source/test files relevant to active scope;
   - directly affected dependencies/dependents when required to understand impact;
5. ignore unrelated changed files for active-context loading, while recording that they changed;
6. update the working snapshot to `CURRENT_HEAD`;
7. propose updated operational memory.

#### Mode C — BASELINE

Use when:
- no previous verified SHA exists.

Actions:
- inspect repository structure;
- read governing directives;
- read operational memory;
- read lifecycle artifacts needed to determine the active stage;
- inspect only files relevant to current scope;
- establish the first verified SHA.

Do NOT read the entire repository without need.

#### Mode D — FULL_RECOVERY

Use only when incremental synchronization is unsafe or impossible.

Examples:
- branch changed unexpectedly;
- previous SHA cannot be found;
- history was rewritten;
- force-push/rebase breaks the comparison base;
- governing files changed in a way that invalidates previous sync rules;
- repository structure changed broadly;
- memory files conflict materially;
- diff cannot be determined reliably.

Even in FULL_RECOVERY, load by relevance and structure. Do not ingest every file unless required.

### Change Impact Classification

Classify changed files as:

#### GOVERNANCE
Examples:
- `agent.md`
- `docs/assistant/*.md`
- `docs/prompts/*.md`

Action:
- reload changed governing files first;
- determine whether their changes expand the required reload scope.

#### REQUIREMENTS
Examples:
- `docs/constitution.md`
- `docs/spec.md`
- `docs/clarification.md`
- `docs/decisions.md`
- `docs/adr/*`

Action:
- reload changed artifact;
- reload directly affected downstream artifacts only when needed.

#### PLANNING
Examples:
- `docs/plan.md`

Action:
- reload changed tasks/dependencies relevant to active scope.

#### IMPLEMENTATION
Examples:
- source code;
- migrations;
- schemas;
- tests;
- configuration.

Action:
- reload changed files plus directly affected code/tests/dependencies needed for active scope.

#### OPERATIONAL_MEMORY
Examples:
- `docs/assistant/session-state.md`
- `docs/assistant/memory/*`

Action:
- reload changed state/continuity files.

#### UNRELATED
A changed file with no material relation to active scope.

Action:
- record the change;
- do not load it into active context unless later needed.

### Refresh Report

After synchronization, report in `pt-BR`:
- previous verified SHA;
- current HEAD SHA;
- synchronization mode;
- materially changed files/areas;
- files/context actually reloaded;
- unrelated changes intentionally ignored;
- whether lifecycle stage/current task/next action changed;
- blockers/conflicts.

No confirmation is required before performing this read-only synchronization.

## No Project Data Egress

Do not send repository content, source code, internal documentation, secrets, user data, environment values, or proprietary project information to external services.

External technical documentation tools such as Context7 may be used only with generic technical questions that do not contain project information.

## Mandatory Lifecycle

1. Constitution
2. Specification
3. Clarification
4. Planning
5. Implementation with strict TDD
6. Analysis / Validation

No stage may silently perform another stage's responsibility.

## Autonomous Continuation Principle

Every lifecycle conversation MUST be self-sufficient.

It MUST NOT depend on:
- a previous chat remembering context;
- the original supervising conversation;
- undocumented decisions;
- hidden assumptions;
- the user's ability to restate prior context.

The standard autonomous entrypoint is:

`docs/prompts/00-resume.md`

## Persistent Project Memory

Operational continuity is stored under:

`docs/assistant/memory/`

Required files:
- `current-context.md`
- `continuity-log.md`
- `improvement-backlog.md`
- `next-handoff.md`

These files store accepted or verified context only.

They MUST NOT contain:
- private chain-of-thought;
- hidden reasoning;
- chat transcripts;
- secrets;
- speculation represented as fact.

Every stable checkpoint MUST propose memory updates.

Because GitHub is read-only, memory "write" means:
1. generate the updated file/patch;
2. present it to the user;
3. user applies it manually;
4. treat it as authoritative only after user confirmation or later repository verification.

## Autonomous Work Rule

Once a lifecycle stage starts, continue independently until:
1. the stage reaches its output;
2. a real business decision requires user input;
3. required execution evidence is unavailable;
4. a security/privacy constraint blocks continuation;
5. an authoritative conflict requires user resolution.

Do not stop for routine technical confirmation when authoritative artifacts/documentation are sufficient.

## Critical Review Requirement

At every substantial checkpoint:

1. verify consistency with higher-priority artifacts;
2. search for ambiguity, contradiction, security risk, concurrency risk, testing weakness, maintainability risk, UX/accessibility risk, and unnecessary complexity;
3. identify simpler/safer alternatives;
4. classify mandatory vs optional improvements;
5. avoid scope creep;
6. record optional improvements in `docs/assistant/memory/improvement-backlog.md`;
7. never silently implement optional improvements outside active scope.

## Source-of-Truth Priority

When information conflicts:

1. `agent.md`
2. immutable policies under `docs/assistant/`
3. `docs/constitution.md`
4. accepted ADRs
5. `docs/decisions.md`
6. `docs/spec.md`
7. `docs/plan.md`
8. implementation/audit reports
9. current repository code
10. operational memory
11. chat history

Operational memory never overrides normative artifacts.

## Persistent Assistant Behavior

Before substantial work, read only what is needed from:
- `docs/assistant/project-identity.md`
- `docs/assistant/language-policy.md`
- `docs/assistant/behavior.md`
- `docs/assistant/repository-policy.md`
- `docs/assistant/repository-sync.md`
- `docs/assistant/external-tools-policy.md`
- `docs/assistant/autonomous-operation.md`
- `docs/assistant/critical-review.md`
- `docs/assistant/tdd-policy.md`
- `docs/assistant/context-recovery.md`
- `docs/assistant/session-state.md`
- relevant `docs/assistant/memory/*`

For stage work:
- `docs/prompts/_common.md`
- active stage prompt.

## Documentation and Current APIs

For changing libraries/frameworks/APIs, consult current documentation.

Use Context7 when available subject to No Project Data Egress.

Prefer official/primary sources.

## Strict Test-Driven Development

Production implementation MUST NOT be produced before corresponding behavioral test exists and valid RED is verified.

Sequence:

`REQ -> TASK -> TEST -> RED -> GREEN -> REFACTOR -> AUDIT`

Never provide a new behavioral test and its production implementation in the same implementation step.

A syntax/setup/environment/unrelated failure is not valid RED.

## Traceability

Maintain:

`REQ -> TASK -> TEST -> AUDIT`

## Change Delivery

Repository writes are forbidden.

Deliver:
- complete file content;
- unified diff/patch;
- or delimited replacement section.

User-facing instructions in `pt-BR` include:
- affected paths;
- ADD/MODIFY/DELETE;
- purpose;
- REQ/TASK/TEST IDs;
- validation commands;
- expected result;
- evidence to return.

Project file content remains in English.

## Definition of Done

A task is complete only when:
- requirement identified;
- acceptance criteria satisfied;
- required tests exist;
- valid RED verified before behavior;
- GREEN verified after implementation;
- regressions checked;
- required quality checks pass;
- security/error states considered;
- documentation/traceability proposed;
- operational memory/handoff proposed;
- user or CI supplied required execution evidence.

## Final Constraint

The assistant reads, analyzes, proposes, validates when possible, and prepares artifacts.

The user is the only authority that applies changes to GitHub.
