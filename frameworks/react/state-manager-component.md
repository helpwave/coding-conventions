# State Manager Component

## Rules

1. A state-manager component **MUST** implement this interface:

```ts
type StateManagerInterface<T, E> = {
  state: T;
  onStateChange?: (value: T) => void;
  onStateEvent?: (event: E) => void;
};
```

2. A state-manager component **MUST** provide `state` to its consumers.
3. A consumer **MUST** be able to send an event through `onStateEvent`.
4. A state-manager component **MUST** send each updated state through `onStateChange`.
5. A state-manager component **MUST** accept children.
6. A state-manager component **MUST** render only `Context.Provider`.
7. A state-manager component **MUST NOT** render an HTML element or a React Native element.

## Applies to

React components whose type is State manager. `[[frameworks/react/component.md]]`

## Exceptions

None.

## Examples

### Good

```tsx
type CounterState = { count: number };
type CounterEvent = { type: "increment" };

function counterReducer(state: CounterState, event: CounterEvent): CounterState {
  if (event.type === "increment") {
    return { count: state.count + 1 };
  }
  return state;
}

function CounterRoot({
  state,
  onStateChange,
  onStateEvent,
  children,
}: StateManagerInterface<CounterState, CounterEvent> & { children?: ReactNode }) {
  const onStateEventRef = useRef(onStateEvent)
  onStateEventRef.value = onStateEvent
  const onStateChangeRef = useRef(onStateChange)
  onStateChangeRef.value = onStateChange

  const handleEvent = useCallBack((event: CounterEvent) => {
	onStateEventRef.current?.(event);
    
    if(onStateChange.current)
	    onStateChangeRef.current.(counterReducer(state, event));
  }, []);

  return (
    <CounterContext.Provider value={{ state, onEvent: handleEvent }}>
      {children}
    </CounterContext.Provider>
  );
}
```

### Bad

```tsx
function InputRoot({ children }: { children: ReactNode }) {
  return <div>{children}</div>;
}
```
