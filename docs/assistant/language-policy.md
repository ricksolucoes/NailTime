# Immutable Language Policy

## Status

`FOUNDATIONAL / IMMUTABLE`

This policy is a project invariant.

No lifecycle stage, prompt, task, ADR, implementation decision, or future convention may weaken or override it.

## User Interaction Language

All direct communication with the user MUST be in Brazilian Portuguese (`pt-BR`).

This includes:

- questions;
- answers;
- explanations;
- summaries;
- status updates;
- errors and warnings;
- clarification requests;
- testing instructions;
- validation instructions;
- implementation guidance;
- review guidance;
- decisions presented for approval.

If the user provides English code, logs, identifiers, documentation excerpts, or technical terms, preserve and interpret those technical elements while keeping the surrounding conversation in `pt-BR`.

## Internal Project Language

All project-authored internal artifacts MUST be written in English.

This includes:

- operating directives;
- assistant behavior files;
- lifecycle prompts;
- source code;
- tests and test names;
- code comments when appropriate;
- documentation;
- architecture records;
- requirements;
- clarification records;
- decisions;
- plans;
- implementation reports;
- audit reports;
- ADRs;
- schemas;
- configuration documentation;
- project-authored skills;
- technical metadata.

## Technical Tokens

Established technical tokens remain unchanged and are not translated.

Examples:

- `React`
- `Fastify`
- `PostgreSQL`
- `useEffect`
- `appointmentId`
- `DATABASE_URL`
- `docs/spec.md`
- `npm test`

## Boundary

The mandatory boundary is:

`Human I/O = pt-BR`

`Internal project artifacts and engineering structures = English`

User-facing prose that explains an English project artifact MUST be written in `pt-BR`.

Do not expose private chain-of-thought or hidden internal reasoning.
