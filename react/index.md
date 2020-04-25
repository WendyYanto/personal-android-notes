# React

## React.PureComponent

1. Use React.PureComponent will not re-render if props and states value stay the same even though parent component re-renders
2. It compares the old and new value by using shallow comparison (by object reference - it is important to avoid mutation of this object because it could lead the value changes but the references stays the same making comparison in effective), so to make it to render effectively we should use immutable value specially when dealing with objects and arrays.
3. Passing functions as props to children components will create new reference although it performs the same operations. It will make React.PureComponent to be ineffective in doing it’s jobs if the parent components re-renders. In order to solve this problems, we should initiate once the functions and store it. React provides useful hooks for this usecase which is by using ```useCallback(() => myFunc(), [...myFuncDependencies])```

## React.Memo

It helps to avoid re-rendering of React functional components by caching. It only changes when it's dependencies change. Example:

```javascript
function areEqual(prev, next) {
    return prev.value === next.value
}
const MemoizedComponent = React.memo(Component, areEqual);
```

## ShouldComponentUpdate

It is a boolean-return function that accept next prop's update value. This will cause rendering if this function return true.

## React.useMemo

It is react hooks to help developer to cache value and it's dependency (parameter) when executing expensive task that has time complexity of n^2 to 2^n