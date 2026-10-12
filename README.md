# G4DNailTime

G4DNailTime is a manicure and nail designer scheduling platform built around a public booking experience and an administrative management area.

The current GitHub repository is:

`ricksolucoes/NailTime`

Accepted project aliases are:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

All three names refer to the same project. `G4DNailTime` is the canonical project and commercial product name.

The business name, logo, slogan, colors, images, contacts, and other branding shown to an end customer are configurable application data and are not the same thing as the G4DNailTime software product identity.

## Project Source of Truth

This repository is the shared source of truth between independent ChatGPT conversations.

Chat history and model memory are not authoritative project records.

The mandatory lifecycle is:

`Constitution -> Specification -> Clarification -> Planning -> Implementation with strict TDD -> Analysis / Validation`

Project decisions and continuation state must be persisted as repository artifacts rather than depending on a previous conversation.

## Language Boundary

The project has an immutable language rule:

- all direct interaction with the user is in Brazilian Portuguese (`pt-BR`);
- all internal project artifacts are written in English.

Internal artifacts include source code, tests, documentation, prompts, architecture records, requirements, tasks, audits, ADRs, and assistant operating files.

## Repository Safety Model

ChatGPT access to this repository is strictly read-only.

The assistant may inspect repository content but must never create or mutate files, commits, branches, pull requests, issues, releases, comments, or any other remote state.

Every proposed change is returned to the user for manual review, application, execution, testing, and approval.

Project code or repository content must not be transmitted to external services. External documentation tools may be used only with generic technical queries that do not disclose project information.

## Project Operating Files

```text
agent.md

docs/
├── assistant/
│   ├── project-identity.md
│   ├── language-policy.md
│   ├── behavior.md
│   ├── repository-policy.md
│   ├── external-tools-policy.md
│   ├── tdd-policy.md
│   ├── context-recovery.md
│   ├── session-state.md
│   └── handoff-template.md
│
├── prompts/
│   ├── _common.md
│   ├── 01-constitution.md
│   ├── 02-specification.md
│   ├── 03-clarification.md
│   ├── 04-planning.md
│   ├── 05-implementation.md
│   └── 06-validation.md
│
├── adr/
├── constitution.md
├── spec.md
├── clarification.md
├── decisions.md
├── plan.md
├── implementation-report.md
└── audit.md
```

Lifecycle artifacts are created only when their corresponding stage produces an accepted proposal and the user applies it.

## Traceability

Engineering work must preserve explicit traceability:

`REQ -> TASK -> TEST -> AUDIT`

Example:

```text
REQ-APT-014
    ↓
TASK-APT-021
    ↓
TEST-APT-032
    ↓
AUDIT-APT-014
```

A project decision that exists only in chat is not an authoritative project decision until it is represented in the appropriate repository artifact.
