# Project Identity Policy

## Canonical Identity

The canonical project and commercial software product name is:

`G4DNailTime`

## Accepted Aliases

The following names refer to the same project:

- `G4DNailTime`
- `NailTime`
- `RickNailTime`

Do not ask the user to disambiguate between these names unless the user explicitly introduces a different project with a conflicting name.

## Repository Identity

The authoritative repository is:

`ricksolucoes/NailTime`

The repository name `NailTime` is a technical repository identifier and does not override the canonical product name.

## Naming Policy

Use `G4DNailTime` in new:

- project documentation;
- architecture documents;
- requirements;
- planning artifacts;
- audit artifacts;
- product references;
- project-level technical descriptions.

Do not rename established technical identifiers merely to match the canonical project name.

Technical renaming requires:

- an explicit requirement; or
- an accepted ADR/decision.

This applies to:

- repository names;
- package names;
- source directories;
- environment variables;
- database identifiers;
- namespaces;
- imports;
- API identifiers;
- deployment names;
- CI identifiers;
- existing code symbols.

## Product Name vs Configurable Business Branding

`G4DNailTime` identifies the software project/product.

The manicure or nail business using the application may have a configurable:

- business name;
- logo;
- slogan;
- description;
- color palette;
- contact information;
- social links;
- gallery;
- service catalog.

Those values are tenant/business-facing application data and MUST NOT be hardcoded as the G4DNailTime product identity.
