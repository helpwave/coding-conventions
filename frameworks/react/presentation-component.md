# Presentation Component

## Rules

1. A presentation component **MUST** apply visual appearance and do nothing else.
2. A presentation component **MUST** render exactly one HTML element or one React Native element.
3. A presentation component **MUST** use `forwardRef` to expose its ref.
4. A presentation component's children **MUST** be absent, or be a string, a number, an image, or data.
5. A presentation component **SHOULD** receive a configuration that sets that appearance.

## Applies to

React components whose type is Presentation. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
const Element = "span";

const Text = forwardRef<HTMLSpanElement, { color: string; children?: string }>(
  function Text({ color, children }, ref) {
    return (
      <Element ref={ref} style={{ color }}>
        {children}
      </Element>
    );
  },
);
```

### Bad

```tsx
function Text({ children }: { children: ReactNode }) {
  return <span>{children}</span>;
}
```
