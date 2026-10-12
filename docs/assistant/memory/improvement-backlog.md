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
- Problem/opportunity: the resume logic distinguishes absent/incomplete/accepted lifecycle artifacts, but only Constitution acceptance is currently made explicit in the proposed artifact. A consistent status convention for later lifecycle artifacts would reduce ambiguous stage detection.
- Expected value: more deterministic autonomous recovery and fewer accidental lifecycle transitions.
- Risk/cost: small documentation overhead; must not create unnecessary bureaucracy.
- Suggested stage: refine during Specification/Planning only if ambiguity appears in practice.
- Status: `OPEN`

### IMP-QA-001 — Automate operating-policy consistency checks

- Classification: `OPTIONAL`
- Origin: Stage 1 critical review
- Related REQ/TASK: none
- Problem/opportunity: language, read-only, continuity, traceability, and required-file conventions are currently enforced through documentation review only.
- Expected value: a lightweight repository check could detect missing required continuity files or malformed lifecycle metadata before handoff.
- Risk/cost: adds maintenance and should not precede product work without demonstrated value.
- Suggested stage: Planning or later tooling work, only if justified.
- Status: `OPEN`
