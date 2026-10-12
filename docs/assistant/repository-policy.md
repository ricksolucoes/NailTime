# Repository Read-Only Policy

## Repository

Canonical repository:

`ricksolucoes/NailTime`

Canonical project/product name:

`G4DNailTime`

## Access Policy

Repository access by ChatGPT is strictly read-only.

Allowed operations:

- repository inspection;
- source and documentation reads;
- code search;
- commit/diff/PR/issue/release/CI inspection when relevant;
- architecture and implementation analysis based on repository content.

Forbidden operations:

- file creation, update, or deletion in GitHub;
- commits;
- branch creation or updates;
- pull request creation or mutation;
- issue creation or mutation;
- merges;
- tags or release mutations;
- labels;
- comments;
- reactions;
- discussions;
- any other operation that changes remote repository state.

Connector write capabilities MUST NOT be interpreted as permission to use them.

## No Repository Data Egress

Repository content MUST NOT be copied, uploaded, pasted, or transmitted to external tools or services for analysis.

This includes:

- source code;
- documentation;
- configuration;
- test data;
- user data;
- environment values;
- project-specific business rules not already intentionally publicized by the user for that external use.

External documentation services may receive only generic technical queries that do not disclose project information.

## Delivery Model

Every proposed repository change must be sent to the user for manual application.

For each change, explain to the user in `pt-BR`:

1. target path;
2. change type: ADD / MODIFY / DELETE;
3. requirement/task/test identifier when applicable;
4. purpose;
5. local validation command;
6. expected validation result;
7. evidence the user should return.

The proposed project file/patch content itself remains in English.

## Verification

Repository state is considered changed only after:

- the user reports applying the change; or
- a later read-only repository inspection confirms the change exists.

Until then, describe all code and documentation as `proposed`.
