# Session State

> Compact continuation checkpoint.
> Store only accepted/verified facts.
> Do not store chain-of-thought.

## Project

- Canonical name: `G4DNailTime`
- Aliases: `NailTime`, `RickNailTime`
- Repository: `ricksolucoes/NailTime`

## Lifecycle Stage

`STAGE_1_CONSTITUTION`

## Current Scope

Revised Constitution proposal, selected technology baseline, and mandatory cross-stage semantics gates.

## Active Requirement IDs

None. Functional requirements are not created during Stage 1.

## Active Task IDs

None. Implementation tasks are not created during Stage 1.

## Active Test IDs

None. Implementation has not started.

## Last Verified Repository State

- Branch: `main`
- Commit/SHA: `c2530891f0210cbad82eca985cd3332e46d4341c`
- Verification date: `2026-10-12`
- Verified state: repository contains operating policies/prompts only; `docs/constitution.md` is absent.

## User-Directed Stage 1 Revisions Pending Repository Application

Selected technology baseline:
- NestJS `12.x`;
- Prisma `7.x`;
- PostgreSQL;
- Next.js `16.x`;
- frontend TypeScript `7.x`;
- Playwright `1.64.x` for full-system E2E.

Mandatory future gates:
- Stage 2/3 must resolve historical business semantics for mutable appointment-related information.
- Stage 2/3 must resolve authentication/identity product and security semantics.
- Stage 4 must choose technical snapshot and authentication strategies only after those semantics are accepted.

## Historical Semantics State

No business classification has been accepted yet for:
- service name;
- price;
- duration;
- category/description when relevant;
- professional when applicable;
- date/time/timezone;
- relevant customer data;
- appointment status/transitions;
- branding when historical presentation is functionally required.

Stage 2 must classify each applicable item as:
- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

## Authentication / Identity Semantics State

No product classification has been accepted yet for the Stage 2 authentication/identity questions.

Stage 2 must classify each applicable point as:
- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

Constitutional security invariants are not optional.

## Last Verified TDD State

- RED: not started
- GREEN: not started
- REFACTOR: not started

## Stage 1 Output State

- `docs/constitution.md`: revised proposal, not yet authoritative
- Proposed Constitution status: `PROPOSED`
- Acceptance evidence: none

## Open Questions / Blockers

- User review/approval of the revised Constitution package.
- Manual repository application.
- Fresh read-only repository verification after application.

## Next Permitted Action

Review the revised Stage 1 package. Do not start Stage 2 until the Constitution is explicitly approved, recorded as `ACCEPTED`, and verified in the repository.

## Files That Must Be Read Next

- `agent.md`
- relevant `docs/assistant/` policies
- `docs/constitution.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/prompts/_common.md`
- `docs/prompts/01-constitution.md`
- `docs/prompts/02-specification.md` only after Stage 1 acceptance is verified
