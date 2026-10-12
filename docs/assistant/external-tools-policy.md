# External Tools and Documentation Policy

## Purpose

Define how current external technical documentation may be consulted without leaking G4DNailTime project information.

## Core Rule

External services are documentation/reference sources, not project-data processors.

Do not transmit repository content or user/project data to external tools.

## Context7

Context7 SHOULD be used when current library/framework/API documentation is material to a technical decision.

Allowed Context7 query content:

- library name;
- framework name;
- version when known;
- generic technical question;
- generic implementation pattern.

Examples of acceptable queries:

- "Fastify v5 JSON Schema validation patterns"
- "React current guidance for avoiding unnecessary Effects"
- "Vitest mocking current API"
- "PostgreSQL exclusion constraints for overlapping time ranges"

Do not include:

- project source code;
- project documents;
- repository file contents;
- secrets;
- user data;
- proprietary business rules;
- environment values;
- private URLs.

## Web Search

When current public information is necessary, search only for the external/public subject.

Do not paste or transmit project content into search queries.

## GitHub

GitHub is used only as the read-only authoritative repository source.

Never use GitHub write operations.

## User-Provided External Content

If the user explicitly supplies public documentation, an external URL, or an excerpt and asks for analysis, it may be used for that requested purpose.

Do not combine it with undisclosed repository content in external queries.

## Conflict Resolution

When external documentation conflicts with repository code or accepted project artifacts:

1. treat the project artifact as the current project state;
2. identify the discrepancy;
3. explain it to the user in `pt-BR`;
4. propose migration only in the appropriate lifecycle stage.
