# Improvement Backlog

> Non-binding engineering improvement proposals.
> Items here MUST NOT override active requirements or be silently implemented.

## Classification

- `RECOMMENDED`
- `OPTIONAL`
- `DEFERRED`

## Item Format

### `IMP-<domain>-<number> — <title>`

- Classification:
- Origin:
- Related REQ/TASK:
- Problem/opportunity:
- Expected value:
- Risk/cost:
- Suggested stage:
- Status:

---

### IMP-GOV-001 — Add lifecycle artifact status convention

- Classification: `RECOMMENDED`
- Origin: Stage 1 critical review
- Related REQ/TASK: none
- Problem/opportunity: autonomous stage detection distinguishes absent/incomplete/accepted artifacts, but a consistent status convention across lifecycle artifacts would reduce ambiguity.
- Expected value: deterministic recovery and fewer accidental lifecycle transitions.
- Risk/cost: small documentation overhead.
- Suggested stage: refine only if ambiguity appears in practice.
- Status: `OPEN`

### IMP-QA-001 — Automate operating-policy consistency checks

- Classification: `OPTIONAL`
- Origin: Stage 1 critical review
- Related REQ/TASK: none
- Problem/opportunity: selected stack boundaries, required continuity files, and lifecycle metadata are enforced primarily through documentation review.
- Expected value: lightweight repository checks could detect stale baseline references, missing continuity files, or malformed lifecycle metadata.
- Risk/cost: tooling maintenance; must not displace product delivery.
- Suggested stage: Planning or later tooling work only if justified.
- Status: `OPEN`

### IMP-ARCH-001 — Reassess selected major versions only through explicit architecture change

- Classification: `DEFERRED`
- Origin: dependency/version critical review
- Related REQ/TASK: none
- Problem/opportunity: selected technology majors will eventually age while newer majors become available.
- Expected value: controlled upgrades avoid accidental major-version drift while still allowing deliberate modernization.
- Risk/cost: upgrade work and compatibility testing.
- Suggested stage: future maintenance lifecycle through an explicit accepted architecture decision, not initial Planning.
- Status: `OPEN`
