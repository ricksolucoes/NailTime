# G4DNailTime Constitution

## Document Control

- Lifecycle stage: `STAGE 1 — CONSTITUTION`
- Status: `PROPOSED`
- Canonical product name: `G4DNailTime`
- Authoritative repository: `ricksolucoes/NailTime`
- Governing directive: `agent.md`

This Constitution defines project-wide engineering invariants and architectural constraints. It intentionally avoids detailed functional requirements.

A Constitution is considered accepted only when:
1. the user explicitly approves the proposed Constitution;
2. the repository copy records `Status: ACCEPTED`;
3. a later read-only repository inspection verifies that accepted state.

Until all three conditions are satisfied, Stage 2 MUST NOT be treated as active.

## 1. Architectural Principles

1. Prefer the simplest architecture that satisfies accepted requirements and preserves correctness, security, maintainability, and operability.
2. Keep browser concerns, server concerns, domain rules, persistence, and external integrations separated by explicit boundaries.
3. Business invariants MUST be enforced at the authoritative server/database boundary, not only in the client.
4. Architectural decisions with significant long-term consequences MUST be recorded as accepted ADRs before implementation depends on them.
5. Avoid speculative abstractions, distributed-system patterns, event infrastructure, microservices, or additional infrastructure unless justified by accepted requirements.
6. The initial system SHOULD remain deployable as a cohesive application with clearly separated frontend, backend, and database responsibilities.
7. Internal modules SHOULD depend on stable abstractions only where those abstractions reduce coupling or make invariants clearer; abstraction for its own sake is prohibited.

## 2. Baseline Technology Boundary

The selected baseline technology stack is:

- backend: NestJS `12.x`;
- backend data access: Prisma `7.x`;
- database: PostgreSQL;
- frontend: Next.js `16.x`;
- frontend language: TypeScript `7.x`;
- full-system end-to-end testing: Playwright `1.64.x`.

These major/minor families are project constraints, not suggestions. Changing them requires an explicit accepted architectural decision.

Dependency installation MUST pin versions compatible with these selected families. Tooling MUST NOT use an unconstrained `latest` tag when doing so could cross a selected major-version boundary.

Prisma `7.x` is the selected data-access family. Planning and bootstrap work MUST verify the current Prisma 7 installation/migration guidance and explicitly select compatible Prisma 7 package versions rather than accidentally upgrading to a later major.

Next.js is the frontend application framework. NestJS is the authoritative backend application framework. Next.js server capabilities MAY support frontend delivery concerns, but MUST NOT silently become a second source of domain authority or duplicate NestJS business rules.

Prisma is the primary application data-access layer. Database-native PostgreSQL constraints or reviewed migration SQL MAY be used when required to enforce integrity that cannot be expressed safely through Prisma alone.

`DEFERRED DECISION`: exact package patch versions inside the selected families; Node.js runtime version; package manager; repository/workspace layout; validation library; authentication library/provider; unit/integration test frameworks; component library; storage provider; deployment platform; and observability vendor.

## 3. Frontend Boundary

The frontend is implemented with Next.js `16.x` and TypeScript `7.x`.

The frontend is responsible for:

- rendering public and administrative experiences;
- collecting user input;
- providing immediate, accessible client-side feedback;
- managing presentation state;
- invoking authoritative NestJS APIs through explicit contracts;
- presenting loading, empty, success, and error states.

The frontend MUST NOT be the authority for:

- authentication or authorization decisions;
- appointment conflict prevention;
- availability integrity;
- pricing or other authoritative business values when such values exist;
- persistence guarantees;
- upload trust decisions;
- any rule whose violation could corrupt business state.

Next.js Route Handlers, Server Actions, middleware/proxy features, or other server-side frontend capabilities MUST NOT bypass the NestJS domain authority for protected business mutations unless a later accepted ADR explicitly redefines the boundary.

Client-side validation is a usability layer, not a security or integrity boundary.

## 4. Backend Boundary

The backend is implemented with NestJS `12.x`, with Prisma `7.x` as the primary data-access layer and PostgreSQL as the authoritative persistent datastore.

The NestJS backend is the authoritative application boundary for business operations.

It MUST:

- authenticate requests when required;
- authorize every protected operation on the server;
- validate untrusted input;
- enforce domain invariants;
- coordinate persistence and concurrency;
- expose stable error semantics;
- avoid leaking secrets or sensitive internals;
- produce sufficient operational evidence for failures and security-relevant events.

Direct database access from the browser/frontend is prohibited.

Backend modules SHOULD separate transport concerns from domain rules and persistence concerns where doing so improves testability and integrity.

## 5. Domain Organization

Domain concepts MUST be represented explicitly rather than hidden inside UI components, transport handlers, or database-specific code.

At minimum, later stages MUST preserve clear conceptual boundaries around:

- business presentation/configuration;
- services;
- scheduling/availability;
- appointments;
- administrative identity/access;
- gallery/media;
- application customization/settings.

This list defines domain areas, not detailed behavior or data models.

Cross-domain dependencies MUST be deliberate and minimal.

## 6. Server Authority, Data Integrity, and Historical Semantics

1. All state-changing business operations MUST be validated server-side.
2. Integrity rules SHOULD be enforced as close to the data as practical when database constraints can prevent invalid states reliably.
3. Multi-step state changes that must succeed or fail together MUST use transactions or equivalent atomic mechanisms.
4. Database writes MUST be designed for retries and duplicate submissions where such retries are plausible.
5. Referential integrity MUST be preserved through explicit keys and constraints where applicable.
6. Destructive operations MUST not rely on UI affordances as their only safeguard.
7. Historical business records MUST not become semantically false because mutable configuration later changes.

### 6.1 Mandatory Stage 2 Historical-Semantics Gate

The Specification MUST explicitly determine the business semantics of mutable data referenced by an appointment before Planning chooses a persistence strategy.

At minimum, Stage 2 MUST evaluate:

- service name;
- service price;
- service duration;
- service category or description, when relevant to historical meaning;
- professional identity, when that concept exists;
- appointment date/time and timezone;
- customer data relevant to the appointment record;
- appointment status and status transitions;
- branding/presentation data only when a functional requirement requires historically preserving the presentation that existed at that time.

For every evaluated item, the Specification MUST classify it as exactly one of:

- `MUST preserve historical value`;
- `MAY use current value`;
- `NOT REQUIRED in historical snapshot`;
- `UNRESOLVED — requires a business decision`.

The Specification MUST define business semantics, not database schema or snapshot persistence mechanics.

Examples of the required semantic level include questions such as whether an existing appointment keeps the price or duration that was accepted when it was created after the underlying service is later edited.

A decision that changes customer-visible behavior, administrative history, financial meaning, audit meaning, scheduling integrity, or the interpretation of an existing appointment MUST NOT be guessed. It MUST be presented to the user in `pt-BR` with:

- the decision required;
- material impacts of each alternative;
- a technical/product recommendation;
- the exact business choice that requires user authority.

Stage 4 Planning, and not Stage 2, MUST choose the technical persistence strategy after the historical semantics are accepted.

`DEFERRED DECISION`: exact snapshot schema, denormalization strategy, versioning model, copy-on-write behavior, event/history tables, database constraints, and migration mechanics.


## 7. Input Validation

1. Every external input is untrusted.
2. Validation MUST occur at system boundaries using explicit schemas or equivalent deterministic validation.
3. Validation SHOULD reject unknown or malformed values rather than silently coercing them when coercion could create ambiguity.
4. Domain validation and syntactic validation SHOULD remain distinguishable.
5. Validation errors presented to users MUST be actionable without exposing sensitive implementation details.
6. Validation logic that protects business invariants MUST be testable independently of the UI.

## 8. Authentication, Identity, and Authorization

### 8.1 Constitutional Security Invariants

1. Administrative capabilities MUST require authenticated access.
2. Authorization MUST be checked server-side for every protected operation.
3. Administrative endpoints MUST require both authentication and the authorization applicable to the requested action.
4. Authorization MUST be deny-by-default.
5. Passwords MUST never be stored in plaintext.
6. Passwords, tokens, session identifiers, reset secrets, MFA secrets, and equivalent credentials MUST never be logged in plaintext.
7. Secrets MUST never live in source code.
8. Authentication failures MUST not expose unnecessary account-existence or sensitive internal-state information.
9. A deactivated or revoked administrative identity MUST NOT retain administrative access through an otherwise valid existing session/token.
10. Authentication/session revocation semantics MUST fail safely.
11. Abuse protection for authentication endpoints is required before production; the exact mechanism is deferred.
12. Security guarantees are mandatory even when the concrete mechanism is deferred.

### 8.2 Mandatory Stage 2/3 Product-Semantics Gate

The Specification, with Clarification when required, MUST define the product/security semantics before Planning selects an authentication implementation.

At minimum, Stage 2 MUST evaluate:

- who must authenticate;
- whether the public area requires a customer account;
- whether customers may book without registration;
- who may access the administrative area;
- whether there is one administrator or multiple administrative users;
- whether separate professionals exist;
- whether professionals have their own login;
- whether different permission levels exist;
- which actions require authentication;
- which actions require specific authorization;
- behavior for incorrect login;
- required protection against abusive authentication attempts;
- logout/session termination;
- session expiration semantics;
- password change;
- access recovery;
- access revocation;
- behavior when a user is deactivated;
- whether MFA is required;
- minimum audit requirements for sensitive administrative actions.

For every evaluated item, Stage 2 MUST classify it as exactly one of:

- `REQUIRED`;
- `NOT REQUIRED`;
- `OPTIONAL`;
- `UNRESOLVED — requires a business decision`.

The assistant MUST NOT turn implementation choices into unnecessary product questions. In particular, Specification MUST NOT ask the user to choose between JWT, HttpOnly cookies, server-side sessions, OAuth/OIDC providers, token formats, password-hashing libraries, session stores, email providers, CSRF implementation mechanisms, token rotation mechanisms, or concrete MFA technologies unless an accepted business requirement genuinely makes that product-sensitive.

When a product choice materially affects security, customer experience, administrative access, permissions, recovery, or audit behavior, the assistant MUST explain the risks and tradeoffs in `pt-BR`, provide a recommendation, and ask only for the actual business decision.

Stage 4 Planning MUST choose the technical authentication strategy only after the accepted product/security semantics are available and after current official technology documentation has been checked.

`DEFERRED DECISION`: JWT versus cookie/session mechanics; server-side session storage; OAuth/OIDC provider; authentication library; concrete password-hashing algorithm/library; token format; session storage technology; email provider; concrete CSRF mechanism; token rotation mechanism; and concrete MFA implementation.


## 9. Error Semantics

1. Errors MUST have stable machine-readable categories at API boundaries.
2. User-facing messages MUST be understandable and must not expose stack traces, SQL, secrets, or internal identifiers unnecessarily.
3. Operational logs MAY contain richer diagnostic context but MUST follow privacy and secret-redaction rules.
4. Expected domain conflicts MUST be distinguishable from infrastructure failures.
5. Unexpected server failures MUST fail safely and return a generic response.
6. Error handling MUST preserve sufficient context for diagnosis through safe correlation identifiers or equivalent mechanisms when introduced.

## 10. Dates, Time, and Timezones

1. Scheduling logic MUST use explicit timezone semantics.
2. The system MUST NOT rely on server local time, browser local time, or implicit JavaScript date parsing as a business invariant.
3. Instants persisted as timestamps MUST use an unambiguous representation.
4. Business-local calendar concepts MUST retain the intended business timezone context.
5. Daylight-saving transitions and timezone offset changes MUST not silently create duplicate, missing, or shifted appointments.
6. Date/time serialization at API boundaries MUST use documented, unambiguous formats.
7. Tests MUST cover relevant boundary conditions when scheduling behavior is implemented.

`DEFERRED DECISION`: canonical business timezone configuration model and the exact persistence representation for local schedule templates.

## 11. Scheduling Concurrency and Integrity

Scheduling integrity is a critical invariant.

1. The authoritative system MUST prevent conflicting appointments even under concurrent requests.
2. Availability shown to a client is advisory until the server commits the booking operation.
3. Conflict prevention MUST be enforced transactionally and/or through database constraints or locking semantics strong enough to prevent double-booking.
4. A read-then-write sequence without a concurrency-safe guard is prohibited for conflict-sensitive booking.
5. Appointment duration and blocking rules, once specified, MUST participate consistently in conflict checks.
6. Administrative and public scheduling operations MUST share the same authoritative conflict model.
7. Concurrency behavior MUST have automated tests at the appropriate level before the scheduling scope is considered complete.

`DEFERRED DECISION`: exact overlap algorithm, locking strategy, PostgreSQL exclusion constraint strategy, isolation level, and retry policy. Planning MUST choose the simplest mechanism that proves the accepted scheduling invariants.

## 12. Database Principles

1. PostgreSQL is the authoritative persistent datastore unless an accepted ADR states otherwise.
2. Schema migrations MUST be deterministic, reviewable, and version-controlled.
3. Production schema changes MUST not depend on automatic destructive synchronization.
4. Constraints, indexes, uniqueness rules, and foreign keys MUST reflect accepted integrity requirements.
5. Migrations that may lose or reinterpret data require explicit migration and rollback/forward-recovery planning.
6. Application code MUST use parameterized queries or a safe query abstraction.
7. Database credentials and connection strings MUST remain outside source control.
8. Seed data, when used, MUST be clearly separated from production data assumptions.

`DEFERRED DECISION`: ORM/query builder and migration tooling.

## 13. Upload and Storage Boundary

1. Uploaded files are untrusted input.
2. The server MUST validate permitted media type, size, and other accepted constraints before treating an upload as valid.
3. File names supplied by users MUST NOT become trusted storage paths.
4. Storage identifiers SHOULD be generated by the system.
5. Public delivery and administrative upload permissions MUST be separated.
6. Storage configuration and credentials MUST remain outside source control.
7. Upload handling MUST prevent path traversal and equivalent filesystem/object-key manipulation.
8. The system MUST define safe handling for unsupported or malformed content before media upload functionality is production-ready.

`DEFERRED DECISION`: local filesystem versus object storage, image transformation pipeline, malware scanning requirements, retention rules, and CDN strategy.

## 14. Theming and Design Tokens

1. Business branding is runtime/configurable data and MUST remain distinct from the G4DNailTime product identity.
2. Visual customization SHOULD be expressed through a bounded token/configuration model rather than arbitrary executable CSS or HTML.
3. Configurable colors and visual tokens MUST preserve accessibility requirements.
4. The frontend SHOULD centralize design tokens to avoid uncontrolled style duplication.
5. User-provided customization MUST NOT permit script execution or unsafe markup injection.

`DEFERRED DECISION`: exact token set, theme persistence model, and customization surface.

## 15. Responsive Design

1. Public booking and administrative interfaces MUST remain usable on supported mobile and desktop viewports.
2. Layouts MUST not depend on a single fixed viewport.
3. Touch targets, text scaling, overflow, dialogs, tables, forms, and navigation MUST be reviewed for smaller screens.
4. Responsive behavior MUST be verified for critical user journeys before release.

Exact breakpoint values are implementation details unless later requirements make them contractual.

## 16. Accessibility

1. Accessibility is a Definition-of-Done concern, not a post-release enhancement.
2. Semantic HTML SHOULD be the default.
3. Interactive controls MUST be keyboard operable.
4. Focus order and focus visibility MUST remain usable.
5. Forms MUST provide programmatically associated labels and accessible error feedback.
6. Color MUST NOT be the only means of conveying essential information.
7. Configurable themes MUST preserve sufficient contrast.
8. Dynamic status changes SHOULD be exposed accessibly when needed.
9. Critical flows MUST be reviewed against applicable WCAG guidance during implementation and validation.

`DEFERRED DECISION`: the exact conformance target/version to be made normative for release. It SHOULD be decided no later than Planning.

## 17. Testing Strategy

Testing MUST favor behavior and invariants over implementation details.

Playwright `1.64.x` is the selected baseline for full-system end-to-end (E2E) testing.

The project SHOULD use a layered strategy appropriate to the implemented scope:

- unit tests for isolated domain logic where valuable;
- integration tests for NestJS/Prisma/PostgreSQL boundaries and integrity rules;
- API tests for transport contracts and authorization;
- frontend/component tests for important Next.js UI behavior;
- Playwright E2E tests for critical full-system user journeys;
- concurrency/integration tests for scheduling conflict guarantees.

E2E coverage MUST NOT be used as a substitute for lower-level tests that can validate domain and database invariants more deterministically.

Tests MUST be deterministic enough to run repeatedly without hidden ordering dependencies.

Critical negative paths, boundary cases, and failure states MUST be tested, not only happy paths.

`DEFERRED DECISION`: exact unit, integration, API, and component test frameworks where Playwright does not apply.


## 18. Strict Test-Driven Development

The mandatory behavioral sequence is:

`REQ -> TASK -> TEST -> RED -> GREEN -> REFACTOR -> AUDIT`

For every new behavior or bug fix:

1. identify the governing requirement and task;
2. create or identify the smallest meaningful behavioral test;
3. verify valid RED caused by the missing/incorrect target behavior;
4. only then propose the minimum production change;
5. verify GREEN with focused and relevant regression tests;
6. refactor only after GREEN;
7. rerun relevant verification;
8. preserve evidence for audit.

A syntax, environment, dependency, discovery, or unrelated failure is not valid RED.

New behavioral tests and their new production implementation MUST NOT be delivered as a single implementation step.

## 19. Observability

1. The application MUST provide enough structured operational evidence to diagnose failures without exposing secrets or unnecessary personal data.
2. Logs SHOULD use stable severity levels and structured context when practical.
3. Security-sensitive events SHOULD be auditable at a level appropriate to accepted requirements.
4. Request correlation SHOULD be available when distributed diagnosis would otherwise be difficult.
5. Health/readiness behavior SHOULD be introduced when deployment requirements justify it.
6. Metrics and traces SHOULD be added based on operational need rather than by default.

`DEFERRED DECISION`: logging library, telemetry stack, metrics platform, tracing platform, retention periods, and alerting thresholds.

## 20. Security and Privacy

1. Apply least privilege to application, database, storage, and deployment access.
2. Secrets MUST be provided through environment/secret-management mechanisms and MUST never be committed.
3. Protected server endpoints MUST enforce authentication and authorization independently of the UI.
4. Output handling MUST prevent injection vulnerabilities appropriate to each context.
5. Database access MUST prevent SQL injection.
6. State-changing browser interactions MUST account for CSRF risk according to the chosen authentication mechanism.
7. Security headers, transport security, dependency hygiene, and secure cookie/token settings MUST be addressed before production release.
8. Personal data collection MUST be limited to accepted product needs.
9. Logs and telemetry MUST minimize personal data and exclude credentials/secrets.
10. Data retention, deletion, backup, and recovery behavior MUST be explicitly decided before production when personal/business data is involved.
11. Security-sensitive defaults MUST fail closed.

`DEFERRED DECISION`: detailed privacy retention periods, backup policy, incident response process, CSP policy, rate limits, anti-automation controls, and compliance obligations. They must be resolved when concrete requirements/deployment context exist.

## 21. Dependencies and Current Documentation

1. Prefer actively maintained dependencies with clear ownership and a justified role.
2. Avoid adding a dependency for functionality that is simpler and safer to implement directly.
3. Pin dependency versions using the package-manager lockfile.
4. Review security advisories and breaking changes before upgrades.
5. For APIs/frameworks whose recommended usage changes, consult current official documentation before implementation decisions.
6. Context7 or external documentation tools may be used only with generic technical questions and MUST NOT receive repository or project data.
7. Repository artifacts remain authoritative project state even when external documentation suggests a migration; migrations require the proper lifecycle decision.

## 22. Configuration and Environments

1. Environment-specific values MUST be externalized from source code.
2. Required configuration MUST be validated at startup where practical.
3. Development defaults MUST NOT silently become unsafe production defaults.
4. Example environment files MUST contain placeholders only, never real secrets.
5. Production behavior MUST not depend on undocumented local-machine state.

`DEFERRED DECISION`: environment topology, hosting platform, secret manager, deployment workflow, and preview/staging strategy.

## 23. Maintainability

1. Prefer clear naming and small cohesive modules.
2. Duplication MAY be preferable to premature abstraction until a stable pattern exists.
3. Dead code and abandoned feature flags SHOULD be removed when safe.
4. Comments SHOULD explain non-obvious rationale or constraints, not restate code.
5. Public contracts and domain invariants SHOULD be discoverable from code and tests.
6. Avoid framework-specific coupling inside core domain rules when separation is inexpensive and materially improves testability.

## 24. Definition of Done

A scoped implementation task is done only when all applicable conditions are satisfied:

- governing requirement identified;
- task traceability established;
- acceptance criteria satisfied;
- required behavioral tests exist;
- valid RED evidence preceded new production behavior;
- GREEN evidence exists after implementation;
- relevant regression tests pass;
- refactor verification passes when refactoring occurred;
- TypeScript checks pass;
- lint/static analysis passes when configured;
- build passes when applicable;
- database migration/integrity impact is verified when applicable;
- authorization/security/error states are considered;
- concurrency is considered for scheduling-sensitive work;
- responsive/accessibility impact is considered for UI work;
- documentation/traceability updates are proposed;
- operational continuity/handoff updates are proposed;
- execution evidence comes from the user, CI, or a permitted local execution environment;
- independent audit is completed when the lifecycle requires it.

No completion claim may be based only on unexecuted code inspection when runtime evidence is required.

## 25. Prohibited Practices

The following are prohibited unless a higher-priority accepted architectural decision explicitly replaces the relevant rule:

- remote GitHub writes by the assistant;
- secrets or real credentials in source control;
- trusting client-side validation for business integrity;
- client-only authorization;
- scheduling conflict checks that are not concurrency-safe;
- implicit timezone assumptions for scheduling;
- unsafe string-built SQL;
- arbitrary executable HTML/CSS/script customization from business data;
- production schema management through destructive auto-sync;
- implementation before valid RED for new behavior/bug fixes;
- silently changing architecture during implementation;
- silently adding optional scope;
- claiming tests/builds/commits passed without evidence;
- sending repository/project data to external services;
- swallowing errors that should change the operation outcome;
- exposing stack traces, SQL details, secrets, or sensitive diagnostics to end users;
- introducing microservices, queues, caches, or additional persistence technologies without demonstrated need and an accepted decision.

## 26. Deferred Decisions Register

The following categories are intentionally not decided by this Constitution:

- exact package patch versions inside the selected major/minor families;
- Node.js runtime version and package manager;
- repository/workspace layout;
- validation library;
- authentication/session implementation mechanics;
- administrative role model details that remain product-sensitive;
- exact API style and versioning convention;
- exact scheduling overlap/locking mechanism;
- exact business timezone configuration model;
- technical historical snapshot persistence strategy;
- upload/storage/CDN/image pipeline;
- detailed privacy retention/deletion policy;
- backup/disaster recovery targets;
- deployment/hosting topology;
- CI/CD implementation;
- observability vendors and retention;
- UI component/design system library;
- exact accessibility conformance target;
- detailed browser/device support matrix;
- rate limiting and abuse-prevention thresholds/mechanisms.

Historical snapshot *business semantics* are NOT deferred to Planning: they MUST be resolved in Specification/Clarification.

Authentication and identity *product/security semantics* are NOT deferred to Planning: they MUST be resolved in Specification/Clarification.

Authentication security guarantees are NOT optional or deferred; only the implementation mechanism is deferred.

Each remaining deferred technical item MUST be resolved only when the proper lifecycle stage has enough accepted requirements and evidence. A deferred decision MUST NOT be silently guessed during implementation.


## 27. Constitution Change Control

After acceptance:

1. this Constitution is normative below `agent.md` and immutable assistant policies;
2. material changes require explicit user approval;
3. architecture-impacting changes SHOULD record rationale in an ADR when appropriate;
4. changes MUST not silently weaken security, integrity, TDD, language, or repository-read-only rules;
5. later lifecycle artifacts MUST conform to the accepted Constitution or explicitly surface a conflict.

## 28. Stage 1 Exit Criteria

Stage 1 is complete only when:

- this Constitution has been critically reviewed;
- the user explicitly approves it;
- repository status is changed to `ACCEPTED`;
- continuity artifacts identify Stage 2 as the next permitted stage;
- a fresh read-only repository inspection verifies the accepted Constitution.

Until then, the lifecycle remains in Stage 1.
