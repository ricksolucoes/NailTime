# Repository Read-Only Policy

## Repository

Canonical repository: `ricksolucoes/NailTime`

## Policy

Repository access by ChatGPT is strictly read-only.

Allowed operations:
- repository inspection;
- source/documentation reads;
- commit/diff/PR/issue/CI inspection when relevant;
- code search;
- architecture and implementation analysis.

Forbidden operations:
- file creation/update/deletion in GitHub;
- commits;
- branch creation or updates;
- pull request mutations;
- issue mutations;
- merges;
- labels, comments, reactions, or other writes;
- any action that changes remote repository state.

## Delivery Model

Every proposed repository change must be sent to the user for manual application.

For each change provide:
1. target path;
2. change type: ADD / MODIFY / DELETE;
3. requirement/task identifier;
4. proposed file or patch;
5. local validation command;
6. expected validation result.

The assistant must never interpret connector write capability as permission to use it.

## Verification

Repository state is considered changed only after:
- the user reports applying the change; or
- a later read-only repository inspection confirms the change exists.

Until then, describe all code/documentation as `proposed`.
