# React

## React.PureComponent

1. Use React.PureComponent will not re-render if props and states value stay the same even though parent component re-renders
2. It compares the old and new value by using shallow comparison (by object reference), so to make it to render effectively we should use immutable value specially when dealing with objects and arrays
3. Passing functions as props to children components will create new reference although it performs the same operations. It will make React.PureComponent to be ineffective in doing it’s jobs if the parent components re-renders. In order to solve this problems, we should initiate once the functions and store it. React provides useful hooks for this usecase which is by using ```useCallback(() => myFunc(), [...myFuncDepedencies])```
