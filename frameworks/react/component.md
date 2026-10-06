# Component

## Rules

1. A component **MUST** be exactly one of the types in this table:

| Type          | Convention                                      |
| ------------- | ----------------------------------------------- |
| Presentation  | [[frameworks/react/presentation-component.md]]  |
| Layout        | [[frameworks/react/layout-component.md]]        |
| Interaction   | [[frameworks/react/interaction-component.md]]   |
| Data input    | [[frameworks/react/data-input-component.md]]    |
| State manager | [[frameworks/react/state-manager-component.md]] |
| Aggregate     | [[frameworks/react/aggregate-component.md]]     |
2. A component that is not an aggregate **MUST NOT** render more than one HTML element or React Native element.
3. A component that is not an aggregate **MUST** render that platform element from a variable, or render only `children`.

## Applies to

React components.

## Exceptions

- An aggregate component **MAY** render more than one HTML element or React Native element.
- A state-manager component renders `Context.Provider` and does not render a platform element variable or `children`.

## Examples

### Good

```tsx
<button type="button">Save</button>
```

The `button` is an interaction component. Its label is a string, not a second interaction component.

### Bad

```tsx
function SaveButton() {
  return (
    <div>
      <button type="button">Save</button>
    </div>
  );
}
```

`SaveButton` renders two platform elements and is not an aggregate.
