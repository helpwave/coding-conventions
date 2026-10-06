# Finite String Sets

## Rules

1. A finite set of string values **MUST** use this declaration, where `<name>` is the set name in camelCase and `<Name>` is the set name in PascalCase:

```ts
const <name>Values = ["value1", "value2"] as const;

export type <Name> = (typeof <name>Values)[number];

const allowed<Name>Values: ReadonlySet<string> = new Set(<name>Values);

function is<Name>Value(value: unknown): value is <Name> {
  if (typeof value !== "string") return false;
  return allowed<Name>Values.has(value);
}

export const <Name>Utils = {
  array: <name>Values,
  set: allowed<Name>Values,
  typeCheck: is<Name>Value,
};
```

## Applies to

TypeScript production code that defines a finite set of string values.

## Exceptions

None.

## Examples

### Good

```ts
const aValues = ["value1", "value2"] as const;

export type A = (typeof aValues)[number];

const allowedAValues: ReadonlySet<string> = new Set(aValues);

function isAValue(value: unknown): value is A {
  if (typeof value !== "string") return false;
  return allowedAValues.has(value);
}

export const AUtils = {
  array: aValues,
  set: allowedAValues,
  typeCheck: isAValue,
};
```

### Bad

```ts
enum A {
  Value1 = "value1",
  Value2 = "value2",
}
```

## Reasoning

A TypeScript `enum` creates a runtime object and a separate type namespace. The array, set, and type guard keep the allowed strings as data that can be iterated and checked.
