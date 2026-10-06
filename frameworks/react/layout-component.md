# Layout Component

## Rules

1. A layout component **MUST** only arrange or stack the components it contains.
2. A layout component **MAY** contain any component.
3. A layout component **MUST NOT** handle interaction.
4. Interaction with a layout **MUST** be handled by one of its children or by its parent.
5. A layout component **MUST** use `forwardRef` to expose its ref.

## Applies to

React components whose type is Layout. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
const Element = "div";

const ButtonRow = forwardRef<HTMLDivElement, { children?: ReactNode }>(
  function ButtonRow({ children }, ref) {
    return (
      <Element ref={ref}>
        {children}
      </Element>
    );
  },
);
```

`ButtonRow` is a layout component. Each child `button` is an interaction component.

### Bad

```tsx
<div onClick={onSelect}>
  <button type="button">Previous</button>
  <button type="button">Next</button>
</div>
```
