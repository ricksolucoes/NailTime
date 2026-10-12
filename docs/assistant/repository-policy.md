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

## Synchronization Policy

Repository refresh is incremental by default.

Read and obey:

`docs/assistant/repository-sync.md`

The exact user phrase:

`Atualizei o GitHub do NailTime.`

forces synchronization from the last verified SHA to current HEAD.

It does not require loading the entire repository.

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
