# Critical Review Policy

## Purpose

Require active self-critique and continuous engineering quality review.

## Mandatory Review Dimensions

At every substantial checkpoint inspect for:

### Requirements
- ambiguity;
- contradiction;
- missing acceptance criteria;
- undefined states;
- hidden assumptions.

### Architecture
- unnecessary coupling;
- premature complexity;
- weak boundaries;
- data-integrity risks;
- migration risks.

### Security and Privacy
- authentication/authorization gaps;
- validation gaps;
- secret exposure;
- unsafe uploads;
- insecure defaults;
- privacy/data retention risks.

### Scheduling Integrity
- race conditions;
- double-booking;
- timezone defects;
- duration overlap;
- stale availability;
- historical snapshot inconsistencies.

### Testing
- missing RED evidence;
- weak assertions;
- happy-path-only coverage;
- missing negative/boundary tests;
- brittle tests;
- implementation-coupled tests.

### UX and Accessibility
- unnecessary friction;
- unclear feedback;
- inaccessible controls;
- keyboard/focus issues;
- loading/error/empty states;
- mobile/responsive problems.

### Maintainability
- duplication;
- excessive abstraction;
- unclear naming;
- dead code;
- unnecessary dependencies;
- weak module boundaries.

## Classification

Findings must be classified as:

- `MANDATORY` — required to satisfy specification, constitution, security, correctness, or Definition of Done.
- `RECOMMENDED` — meaningful improvement with strong value.
- `OPTIONAL` — useful but not required for current scope.
- `DEFERRED` — intentionally postponed.

## Scope Protection

Do not silently implement RECOMMENDED/OPTIONAL improvements during an unrelated task.

Record them in:

`docs/assistant/memory/improvement-backlog.md`

Mandatory defects affecting the active scope must be addressed or explicitly block completion.

## Self-Critique Before Delivery

Before delivering a stage artifact or implementation proposal, verify:

1. Does it obey higher-priority project artifacts?
2. Did it invent any requirement?
3. Is there a simpler solution?
4. What can fail?
5. What is not tested?
6. What security/data-integrity risk remains?
7. What assumption remains unverified?
8. What should the next conversation know?
