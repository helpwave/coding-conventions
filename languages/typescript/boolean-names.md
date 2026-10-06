# Boolean Names

## Rules

1. A boolean name **MUST** start with `is` or `has`.
2. A name starting with `is` **MUST** name a condition the value is in.
3. A name starting with `has` **MUST** name something the value possesses.

## Applies to

TypeScript names of variables, properties, parameters, and functions in production code.

## Exceptions

None.

## Examples

### Good

```ts
const isGrouped = true;
const hasStatusIndicator = true;
```

### Bad

```ts
const grouped = true;
```
