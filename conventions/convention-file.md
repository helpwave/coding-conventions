# Convention File

## Rules

1. A convention file **MUST** be unambiguous.
2. A convention file **MUST** only regard one topic.
3. A dependency of a convention on another convention **MUST** be included in the text like this [[conventions/convention-file]]
4. A convention file **MUST** not be named `index.md`
5. A convention file **MUST** follow this table for its structure.

| Name | Function | Is required |
| --- | --- | --- |
| `# <name>` | Names the subject of the convention. | true |
| `## Rules` | States the required behavior. | true |
| `## Applies to` | States where the rules apply. | true |
| `## Exceptions` | States the allowed deviations from the rules. | true |
| `## Examples` | Shows behavior that `## Rules` already decides. | true |
| `## Reasoning` | States why a rule is applied in that way. | false |

## Applies to

All convention documents in this repository.

## Exceptions

None.

## Examples

### Good

```md
# Service Dependencies

## Rules

- Services MUST receive external dependencies through their parameters.

## Applies to

Backend application services.

## Exceptions

None.

## Examples

### Good

A service takes its dependencies as parameters.
```

### Bad

```md
# Service Dependencies

Services receive external dependencies through their parameters so that tests can replace them.
```

## Reasoning

An agent takes required behavior from `## Rules`, `## Applies to`, and `## Exceptions`. Requirements placed only in examples or prose are skipped.
