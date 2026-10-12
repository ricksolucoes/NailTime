# Next Handoff

## Status

`STAGE_1_REVISED_PROPOSAL_AWAITING_ACCEPTANCE`

## Next Stage

Remain in `STAGE_1_CONSTITUTION` until the revised Constitution is explicitly accepted and verified.

## Objective

Preserve the selected technology stack and the mandatory cross-stage decisions so no future conversation can silently revert to a superseded baseline or postpone business semantics that must be settled before Planning.

## Required Inputs

- `agent.md`
- relevant `docs/assistant/` policies
- `docs/assistant/session-state.md`
- `docs/assistant/memory/current-context.md`
- `docs/assistant/memory/continuity-log.md`
- `docs/assistant/memory/improvement-backlog.md`
- `docs/prompts/_common.md`
- `docs/prompts/00-resume.md`
- `docs/prompts/01-constitution.md`
- `docs/constitution.md` when present

## Selected Technology Baseline in the Revised Proposal

- backend: NestJS `12.x`;
- data access: Prisma `7.x`;
- database: PostgreSQL;
- frontend: Next.js `16.x`;
- frontend language: TypeScript `7.x`;
- full-system E2E: Playwright `1.64.x`.

Do not cross these selected version families through unconstrained `latest` installs.

## Mandatory Historical-Semantics Handoff

Stage 2 MUST evaluate and classify the historical treatment of:
- service name;
- price;
- duration;
- category/description when relevant;
- professional when applicable;
- date/time/timezone;
- relevant customer data;
- appointment status/transitions;
- branding only when a historical presentation requirement exists.

Allowed classifications:
- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

Price and duration MUST be semantically resolved or explicitly escalated before Planning.

Do not choose the storage mechanism during Specification/Clarification.

## Mandatory Authentication / Identity Handoff

Stage 2/3 MUST determine product/security semantics for account requirements, guest booking, admin/professional identities, permissions, protected actions, login failure, abuse protection, logout, expiry, password change/recovery, revocation/deactivation, MFA, and sensitive-admin audit requirements.

Allowed classifications:
- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

Do not ask the user to choose routine technical mechanisms such as JWT/cookies, session storage, hashing library, OAuth provider, CSRF mechanism, token rotation, or MFA implementation unless the choice itself is product-sensitive.

## Mandatory Stage 4 Handoff

After accepted semantics:
- choose the technical historical snapshot strategy;
- choose the technical authentication strategy;
- consult current official documentation;
- optimize for integrity, simplicity, maintenance, queries, migrations, and consistency;
- preserve accepted behavior instead of changing requirements to fit a preferred implementation;
- explicitly pin compatible Prisma `7.x` packages.

## Constitutional Security Guarantees to Preserve

- passwords never stored in plaintext;
- server-side deny-by-default authorization;
- authenticated/authorized administrative endpoints;
- revoked/deactivated admin identities lose effective access;
- safe authentication error behavior;
- no source-code secrets;
- abuse protection required before production.

## Active REQ/TASK/TEST

None.

## Verified Repository Evidence

Last verified remote state:
- branch: `main`;
- commit: `c2530891f0210cbad82eca985cd3332e46d4341c`;
- Constitution absent at that snapshot.

The revised files are local proposals only until the user applies them.

## Blockers

- explicit user approval of the revised proposal;
- manual application;
- fresh read-only repository verification.

## Next Permitted Action

If approved, prepare/apply the accepted Stage 1 state manually. After the repository update signal, refresh the repository and verify the accepted Constitution and updated prompts/memory before loading Stage 2.
