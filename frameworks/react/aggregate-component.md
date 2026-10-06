# Aggregate Component

## Rules

1. An aggregate component **MUST** compose other components into one component.
2. An aggregate component **MUST** expose each composed component as a static member.
3. An aggregate component **MUST** accept a prop named `<member>Props` for each static member, where `<member>` is that member's name in camelCase.
4. An aggregate component **MUST** accept a ref named `<member>Ref` for each static member, where `<member>` is that member's name in camelCase.
5. That ref **MUST** be passed to that static member.
6. An aggregate **MAY** accept a prop that a composed component also accepts.
7. That prop **MUST** be passed only to the composed components that use it.
8. The `<member>Props` spread **MUST** come after those props, so `<member>Props` overwrites them.
9. An aggregate component **MAY** render more than one HTML element or React Native element.

## Applies to

React components whose type is Aggregate. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
type DialogProps = {
  isOpen?: boolean;
  rootRef?: ComponentRef<typeof Dialog.Root>;
  rootProps?: ComponentProps<typeof Dialog.Root>;
  triggerRef?: ComponentRef<typeof Dialog.Trigger>;
  triggerProps?: ComponentProps<typeof Dialog.Trigger>;
  overlayRef?: ComponentRef<typeof Dialog.Overlay>;
  overlayProps?: ComponentProps<typeof Dialog.Overlay>;
  headerRef?: ComponentRef<typeof Dialog.Header>;
  headerProps?: ComponentProps<typeof Dialog.Header>;
  contentRef?: ComponentRef<typeof Dialog.Content>;
  contentProps?: ComponentProps<typeof Dialog.Content>;
}

function Dialog({
  isOpen,
  rootRef,
  rootProps,
  triggerRef,
  triggerProps,
  overlayRef,
  overlayProps,
  headerRef,
  headerProps,
  contentRef,
  contentProps,
}: DialogProps) {
  return (
    <Dialog.Root ref={rootRef} isOpen={isOpen} {...rootProps}>
      <Dialog.Trigger ref={triggerRef} {...triggerProps}>
        Open
      </Dialog.Trigger>
      <Dialog.Overlay ref={overlayRef} {...overlayProps}>
        <Dialog.Header ref={headerRef} {...headerProps}>
          Title
        </Dialog.Header>
        <Dialog.Content ref={contentRef} {...contentProps}>
          Body
        </Dialog.Content>
      </Dialog.Overlay>
    </Dialog.Root>
  );
}
```

`isOpen` is passed only to `Dialog.Root`, the composed component that uses it. Each member receives its `<member>Ref`, such as `triggerRef` on `Dialog.Trigger`. `rootProps` is spread after `ref` and `isOpen`, so it overwrites them.
