# G4DNailTime — Stage 4: Planning

## Responsibility

Perform EXCLUSIVELY:

`STAGE 4 — PLANNING`

## Inputs

Read:
- governing policies;
- operational memory;
- Constitution;
- Specification;
- Decisions;
- relevant accepted ADRs.

Proceed only when blocking clarification is sufficiently resolved.

## Objective

Convert approved requirements into small dependency-aware independently reviewable implementation tasks.

Choose technical strategies only after their governing business/security semantics are accepted.

Do not implement code.

## Selected Technology Constraints

Planning MUST preserve the accepted baseline:
- backend: NestJS `12.x`;
- Prisma `7.x`;
- PostgreSQL;
- frontend: Next.js `16.x`;
- frontend TypeScript: `7.x`;
- full-system E2E: Playwright `1.64.x`.

Before bootstrap/implementation tasks are finalized, verify current official documentation and choose explicit compatible package versions inside these families.

Do not use unconstrained `latest` where it could cross an accepted version boundary.

## Historical Snapshot Technical Planning

Only after Specification/Clarification has accepted the semantic classification for mutable appointment-related information, choose the technical persistence strategy.

Evaluate at minimum:
- historical integrity;
- schema/data simplicity;
- query ergonomics;
- maintenance cost;
- migration complexity;
- consistency under service/customer/professional changes;
- scheduling correctness;
- audit/financial implications from the accepted semantics.

Planning MAY choose among snapshot columns, normalized historical/versioned records, database constraints, or another appropriate design, but MUST NOT change the accepted business semantics to fit a preferred schema.

Record material architecture consequences in an ADR when warranted.

## Authentication Technical Planning

Only after authentication/identity product semantics are accepted, select the implementation strategy.

Evaluate at minimum:
- NestJS/Next.js boundary;
- server-side authorization enforcement;
- credential storage/hashing;
- session/token revocation;
- deactivated-user invalidation;
- CSRF implications;
- brute-force/abuse protection;
- session expiry;
- recovery flows;
- MFA when required;
- audit requirements;
- operational complexity;
- current official framework/library guidance.

Planning, not Specification, decides technical questions such as cookie/session/JWT mechanics, provider/library selection, session storage, hashing implementation, CSRF mechanism, token rotation, and concrete MFA technology.

Do not weaken constitutional security guarantees for implementation convenience.

## Task Format

Each TASK:
- TASK ID
- title
- objective
- related REQ IDs
- dependencies
- inputs
- expected outputs
- likely files/modules
- required tests
- TDD applicability
- acceptance criteria
- Definition of Done

Prefer small verifiable tasks.

## TDD Planning

Behavior tasks must preserve:

1. RED test step
2. valid RED evidence
3. GREEN implementation step
4. valid GREEN evidence
5. REFACTOR when useful
6. verification

Planning may describe implementation scope but must not produce production code.

Playwright `1.64.x` tasks should cover critical full-system journeys; lower-level tests remain necessary for domain/database invariants where E2E would be slower or less deterministic.

## Critical Self-Review

Before delivery:
- detect tasks that are too large;
- detect unnecessary dependency chains;
- identify risky sequencing;
- identify missing test infrastructure;
- identify migration/data risks;
- verify snapshot storage implements rather than redefines accepted historical semantics;
- verify authentication mechanics implement rather than redefine accepted product/security semantics;
- identify parallelizable work;
- identify opportunities to simplify;
- verify current official documentation for selected framework/library APIs;
- verify Prisma remains on `7.x` and other selected version boundaries are not crossed unintentionally.

## Output

Produce proposed English:
- `docs/plan.md`

Include dependency graph and intended test coverage.

Also propose updated memory/handoff files and improvement backlog if applicable.

Explain recommended execution order in `pt-BR`.

Do not write to GitHub.
