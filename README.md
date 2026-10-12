# G4DNailTime

G4DNailTime is a manicure and nail designer scheduling platform with a public booking experience and an administrative management area.

Repository:

`ricksolucoes/NailTime`

Accepted aliases:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

## Operating Model

The repository is the shared source of truth between independent ChatGPT conversations.

Chat history and model memory are not authoritative project records.

Mandatory lifecycle:

`Constitution -> Specification -> Clarification -> Planning -> Implementation with strict TDD -> Analysis / Validation`

Autonomous entrypoint:

`docs/prompts/00-resume.md`

## Language Boundary

Immutable rule:

- direct user interaction: Brazilian Portuguese (`pt-BR`);
- internal project artifacts: English.

## Repository Safety

ChatGPT repository access is strictly read-only.

## Incremental Repository Synchronization

The exact phrase:

`Atualizei o GitHub do NailTime.`

forces synchronization with GitHub.

Synchronization is SHA-based and incremental:

1. read last verified SHA;
2. read current HEAD;
3. compare the commit range;
4. inspect changed files;
5. reload only changed/directly affected context.

The repository is not fully re-read on every update.

Supported modes:

- `NO_CHANGE`
- `INCREMENTAL`
- `BASELINE`
- `FULL_RECOVERY`

`FULL_RECOVERY` is a fallback only when incremental comparison is unsafe or impossible.

## Persistent Operational Memory

```text
docs/assistant/memory/
├── current-context.md
├── continuity-log.md
├── improvement-backlog.md
└── next-handoff.md
```

The last verified SHA is persisted so future conversations can synchronize incrementally.

## Main Operating Files

```text
agent.md

docs/
├── assistant/
│   ├── project-identity.md
│   ├── language-policy.md
│   ├── behavior.md
│   ├── repository-policy.md
│   ├── repository-sync.md
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

## Traceability

`REQ -> TASK -> TEST -> AUDIT`

A project decision existing only in chat is not authoritative until represented in the repository.
