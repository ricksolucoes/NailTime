# Repository Read-Only Policy

## Repository

`ricksolucoes/NailTime`

## Access Policy

Repository access by ChatGPT is strictly read-only.

Allowed:
- inspection;
- reads;
- code search;
- commit/diff/PR/issue/release/CI inspection.

Forbidden:
- file writes;
- commits;
- branch mutations;
- PR/issue/release mutations;
- merges;
- comments;
- labels;
- reactions;
- any remote state change.

Connector write capability is never permission.

## Mandatory Refresh Command

The exact user phrase:

`Atualizei o GitHub do NailTime.`

forces an immediate repository refresh.

After the phrase:
- invalidate prior repository snapshot;
- re-read root;
- re-read governing policies;
- re-read operational memory;
- re-read current lifecycle artifacts;
- re-read relevant code/tests;
- continue only from refreshed state.

## No Repository Data Egress

Do not transmit repository content to external services.

External documentation services receive only generic technical queries.

## Delivery Model

Every proposed repository change is returned to the user.

User-facing instructions are in `pt-BR`.

Project file/patch content remains in English.

## Verification

Repository state changes only after:
- user confirmation; or
- later read-only inspection verifies it.
