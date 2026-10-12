# External Tools and Documentation Policy

## Core Rule

External services are reference sources, not project-data processors.

Do not transmit repository content or user/project data to external tools.

## Context7

Use Context7 when current library/framework/API documentation materially affects a decision.

Allowed:
- library name;
- version;
- generic technical question;
- generic implementation pattern.

Forbidden:
- project source code;
- repository documents;
- secrets;
- user data;
- environment values;
- private project URLs;
- proprietary project-specific content.

## Web Search

Search only for public/external subjects.

Do not paste repository content into search queries.

## GitHub

GitHub is the read-only authoritative repository source.

Never use write operations.

## Conflict Resolution

When external documentation conflicts with accepted project artifacts:
1. keep project artifact as current project state;
2. identify discrepancy;
3. explain to user in `pt-BR`;
4. propose migration only in the proper lifecycle stage.
