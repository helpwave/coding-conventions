# Rules
## Rules
1. A rule **MUST** use exactly one of these normative keywords: `**MUST**`, `**MUST NOT**`, `**SHOULD**`, `**SHOULD NOT**`, or `**MAY**`
2. The meaning of the normative keywords **MUST** follow from this table's definition:

| Keyword      | Meaning                                                                                              |
| ------------ | ---------------------------------------------------------------------------------------------------- |
| `MUST`       | The behavior is mandatory.                                                                           |
| `MUST NOT`   | The behavior is prohibited                                                                           |
| `SHOULD`     | The behavior is the default, and deviation is allowed when the deviation is justified in the change. |
| `SHOULD NOT` | The behavior is discouraged, and deviation is allowed when the deviation is justified in the change. |
| `MAY`        | The behavior is optional                                                                             |

3.  A rule **MUST** state one requirement that can be checked on its own.
4. A rule **SHOULD** be decidable with yes or no.

## Applies to
Every rule in a convention document in this repository.

## Exceptions
- A rule MAY quote a prohibited term when that rule prohibits the term.

## Examples

### Good
```md
- Services MUST receive external dependencies through their parameters.
```

### Bad
```md
We generally prefer dependency injection.
```

## Why
A reader applies a rule without the surrounding document. Keyword meaning, scope of the requirement, and the facts needed to check it have to be in the rule itself.
