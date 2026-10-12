# Current Context

> Authoritative compact continuation context.
> Store accepted/verified project state only.
> Do not store private chain-of-thought.

## Project

- Name: `G4DNailTime`
- Repository: `ricksolucoes/NailTime`

## Current Lifecycle Stage

`STAGE_1_CONSTITUTION`

## Current Objective

Review and accept the revised Constitution proposal while preserving mandatory future decisions about historical semantics and authentication/identity semantics.

## Selected Technology Baseline

User-directed baseline for the revised Constitution:
- backend: NestJS `12.x`;
- data access: Prisma `7.x`;
- database: PostgreSQL;
- frontend: Next.js `16.x`;
- frontend language: TypeScript `7.x`;
- full-system E2E: Playwright `1.64.x`.

These selections are included in the proposed Constitution but are not repository-authoritative until manually applied and verified.

## Mandatory Stage 2/3 Historical-Semantics Gate

Specification/Clarification must evaluate mutable appointment-related data and classify each applicable item as:
- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

Minimum evaluation set:
- service name;
- price;
- duration;
- category/description when historically relevant;
- professional when applicable;
- date/time/timezone;
- relevant customer data;
- appointment status/transitions;
- branding only when a functional historical-presentation requirement exists.

Price and duration cannot be silently left for Planning. Their business behavior after later service edits must be accepted in Specification/Clarification.

Do not invent the business answer. Product-sensitive choices with customer, admin, financial, audit, or scheduling impact must be presented to the user in `pt-BR` with recommendation and tradeoffs.

## Mandatory Stage 2/3 Authentication / Identity Gate

Specification/Clarification must determine product/security semantics for:
- authentication actors;
- customer account requirement;
- guest booking;
- administrator cardinality;
- professionals and professional logins;
- permission levels;
- authenticated/authorized actions;
- incorrect-login behavior;
- abuse-protection requirement;
- logout;
- session expiry semantics;
- password change;
- recovery;
- revocation;
- deactivated-user behavior;
- MFA requirement;
- minimum sensitive-admin audit requirements.

Each applicable point must be classified:
- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

Do not ask the user to choose routine engineering mechanics such as JWT vs cookies, session store, hashing library, CSRF mechanism, token rotation, or provider selection unless the choice is genuinely product-sensitive.

## Constitutional Security Guarantees Included in the Proposal

- passwords are never stored in plaintext;
- authorization is server-side and deny-by-default;
- administrative endpoints require authentication and applicable authorization;
- inactive/revoked administrative identities cannot retain access through existing sessions/tokens;
- authentication errors do not leak unnecessary sensitive account information;
- secrets never live in source code;
- authentication abuse protection is required before production;
- security guarantees are mandatory even when mechanisms are deferred.

## Mandatory Stage 4 Planning Gates

After semantics are accepted:
- choose the snapshot persistence strategy based on integrity, simplicity, maintainability, query needs, migrations, and consistency;
- choose the authentication implementation strategy based on accepted semantics, architecture, security guarantees, and current official documentation;
- verify current compatible versions inside the selected technology families;
- explicitly remain on Prisma `7.x` rather than using an unconstrained latest major.

## Active Requirements / Tasks / Tests

None. Stage 1 is still active.

## Last Verified Repository Snapshot

- Branch: `main`
- Commit/SHA: `c2530891f0210cbad82eca985cd3332e46d4341c`
- Verified date: `2026-10-12`
- `docs/constitution.md`: absent at the verified snapshot.

## Current Blockers

- revised Constitution approval;
- manual repository application;
- fresh read-only verification.

## Next Permitted Action

Complete Stage 1 acceptance. Only after verification may Stage 2 begin.

## Required Files for Continuation

- `agent.md`
- relevant `docs/assistant/` policies
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/next-handoff.md`
- `docs/prompts/_common.md`
- `docs/prompts/00-resume.md`
- `docs/prompts/01-constitution.md`
- `docs/constitution.md` when present
