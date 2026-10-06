# Data Input Component

## Rules

1. A data-input component **MUST** implement this interface:

```ts
type ControlledInput<T> = {
  value: T;
  onValueChange: (value: T) => void;
};
```

2. A data-input component **MUST** use `forwardRef` to expose its ref.
3. A data-input component's state **MUST** include this interface:
```typescript
type InputState = {
  isInvalid?: boolean;
  isDisabled?: boolean;
  isReadOnly?: boolean;
  isRequired?: boolean;
};
```

## Applies to

React components whose type is Data input. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
const Element = "input";

type TextInputProps = ControlledInput<string> & InputState;

const TextInput = forwardRef<HTMLInputElement, TextInputProps>(
  function TextInput({ value, onValueChange }, ref) {
    return (
      <Element
        ref={ref}
        value={value}
        onChange={(event) => onValueChange?.(event.target.value)}
      />
    );
  },
);
```

### Bad

```ts
type TextInputState = {
  invalid?: boolean;
  required?: boolean;
};
```
