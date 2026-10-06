# Convention Organization

## Rules

1. Conventions **MUST** be organized by folders and files.
2. A folder **MUST** define one grouping.
3. A file other than `index.md` **MUST** define one convention.
4. Each folder **MUST** contain an summarizing `index.md`.
5. An `index.md` **MUST** reference every file other than itself and every folder in that folder in a table with the columns `path` and `content`.
## Applies to

Every folder in this repository that contains conventions.

## Exceptions

None.

## Examples

### Good

```md
# Imports

Import conventions for Hightide packages.

| path | content |
| --- | --- |
| `imports.md` | Import paths and statement order. |
| `design-token-imports.md` | Design token module specifiers. |
```

### Bad

```text
imports/
  imports.md
  design-token-imports.md
```

## Reasoning

An agent can choose the one convention that applies from the folder summary and the `path` / `content` table, without opening every file in the folder.
