# Interaction Component

## Rules

1. An interaction component **MUST** handle user interaction.
2. An interaction component **MUST** be the outermost element that handles that interaction.
3. An interaction component **MUST NOT** contain an interaction component.
4. An interaction component **MUST NOT** contain a data-input component. `[[frameworks/react/data-input-component.md]]`
5. An interaction component **MAY** arrange or stack the components it contains.
6. An interaction component **MAY** apply visual appearance from a configuration.
7. An interaction component **MUST** use `forwardRef` to expose its ref.

## Applies to

React components whose type is Interaction. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
const Element = "button";

const SaveButton = forwardRef<HTMLButtonElement>(
  function SaveButton(_, ref) {
    return (
      <Element ref={ref} type="button">
        Save
      </Element>
    );
  },
);
```

`SaveButton` is the interaction component. The label is not.

### Bad

```tsx
<button type="button">
  <button type="button">Save</button>
</button>
```

## Reasoning

An interaction component can arrange children and apply appearance while its type stays Interaction. The text or icon inside a button is not a second interaction component.
