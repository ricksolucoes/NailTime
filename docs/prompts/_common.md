# G4DNailTime — Common Lifecycle Prompt Contract

This file applies to every G4DNailTime lifecycle stage.

## Project Identity

Canonical project/product name:

`G4DNailTime`

Accepted aliases:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

Repository:

`ricksolucoes/NailTime`

All accepted aliases refer to the same project.

## Immutable Language Boundary

All direct interaction with the user MUST be in Brazilian Portuguese (`pt-BR`).

All internal project artifacts MUST be written in English.

Do not translate established code symbols, paths, commands, APIs, library names, environment variables, identifiers, or other native technical tokens.

This rule cannot be overridden by a stage-specific prompt.

## Mandatory Startup

Before substantial work:

1. read `agent.md`;
2. read the relevant files under `docs/assistant/`;
3. read this file;
4. read the active stage prompt;
5. read only the authoritative lifecycle artifacts required by that stage;
6. inspect only repository files required by the current scope.

If a mandatory policy file is unavailable, tell the user in `pt-BR` and do not silently invent its contents.

## Repository Safety

GitHub access is strictly read-only.

Never create or mutate:

- files;
- commits;
- branches;
- pull requests;
- issues;
- releases;
- comments;
- labels;
- reactions;
- discussions;
- any other remote state.

Return every proposed project change to the user for manual application and testing.

## No Project Data Egress

Do not send repository content, source code, documentation, secrets, user data, or proprietary project information to external services.

Context7 or equivalent current-documentation tools may be used only with generic technical questions that do not contain project content.

## Source of Truth

Use the priority defined in `agent.md`.

Never treat chat history or model memory as authoritative project state.

## Scope Discipline

Perform only the active lifecycle stage.

Do not silently:

- implement during requirements work;
- change requirements during implementation;
- change architecture during coding;
- approve unverified implementation;
- skip TDD gates.

If the required action belongs to another stage, explain this to the user in `pt-BR` and prepare the correct handoff.

## Evidence

Differentiate between:

- verified repository fact;
- accepted project rule;
- proposed change;
- unresolved question;
- user-provided execution evidence;
- unverified assumption.

Never present an assumption as fact.

## Current Documentation

When a technical decision depends on current framework/library/API behavior:

1. consult current official documentation;
2. use Context7 when available;
3. query generically without project data;
4. prefer primary sources;
5. explain relevant conclusions to the user in `pt-BR`.

## Delivery Boundary

User-facing explanation: `pt-BR`.

Project file content/patches: English.

For proposed changes, tell the user in `pt-BR`:

- target path;
- ADD / MODIFY / DELETE;
- purpose;
- relevant REQ/TASK/TEST IDs;
- local validation commands;
- expected result;
- evidence to return.

## Traceability

Maintain:

`REQ -> TASK -> TEST -> AUDIT`
