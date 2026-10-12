# G4DNailTime

G4DNailTime is a manicure and nail designer scheduling platform with a public booking experience and an administrative management area.

Repository:

`ricksolucoes/NailTime`

Accepted project aliases:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

All aliases refer to the same project. `G4DNailTime` is the canonical project and commercial software product name.

## Operating Model

The repository is the shared source of truth between independent ChatGPT conversations.

Chat history and model memory are not authoritative project records.

The mandatory lifecycle is:

`Constitution -> Specification -> Clarification -> Planning -> Implementation with strict TDD -> Analysis / Validation`

The autonomous entrypoint for a new conversation is:

`docs/prompts/00-resume.md`

## Language Boundary

Immutable rule:

- direct user interaction: Brazilian Portuguese (`pt-BR`);
- internal project artifacts: English.

## Repository Safety

ChatGPT repository access is strictly read-only.

Every proposed repository change is returned to the user for manual review, application, execution, testing, and approval.

## Repository Refresh Control Command

The exact phrase:

`Atualizei o GitHub do NailTime.`

forces an immediate fresh read-only repository inspection before any further project work.

## Persistent Operational Memory

Cross-conversation continuity is stored under:

```text
docs/assistant/memory/
├── current-context.md
├── continuity-log.md
├── improvement-backlog.md
└── next-handoff.md
```

These files contain compact accepted/verified project state only. They do not contain private chain-of-thought.

## Operating Files

```text
agent.md

docs/
├── assistant/
│   ├── project-identity.md
│   ├── language-policy.md
│   ├── behavior.md
│   ├── repository-policy.md
│   ├── external-tools-policy.md
│   ├── autonomous-operation.md
│   ├── critical-review.md
│   ├── tdd-policy.md
│   ├── context-recovery.md
│   ├── session-state.md
│   ├── handoff-template.md
│   └── memory/
│       ├── current-context.md
│       ├── continuity-log.md
│       ├── improvement-backlog.md
│       └── next-handoff.md
│
└── prompts/
    ├── _common.md
    ├── 00-resume.md
    ├── 01-constitution.md
    ├── 02-specification.md
    ├── 03-clarification.md
    ├── 04-planning.md
    ├── 05-implementation.md
    └── 06-validation.md
```

Lifecycle artifacts are created as their stages are completed.

## Traceability

`REQ -> TASK -> TEST -> AUDIT`

A project decision that exists only in chat is not authoritative until represented in the repository.
