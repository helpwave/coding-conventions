# Styling Identification

## Rules

1. A component **MUST** expose its styling identity as a class name.
2. A component **MUST NOT** use a data attribute as its styling identity.
3. A data attribute on a component **MUST** represent state or configuration.

## Applies to

React components.

## Exceptions

None.

## Examples

### Good

```tsx
<button className="button" data-disabled="true" data-processing="subtle" />
```

### Bad

```tsx
<button data-name="button" />
```
