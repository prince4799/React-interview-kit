 
  [⬅ Go Back](../Index.md) 
   <h1 style="text-align: center; margin: 0; color:#00fc04; ">What is useMemo in React?</h1>

 * The `useMemo` hook is used to memoize a value that is expensive to compute and prevent 
  unnecessary re-calculation during re-renders. 
 * For example, if a parent component re-renders due to a state change, 
 * a child component might re-render as well even if it doesn't rely on that state directly.
 * If the child component uses expensive computations, we can wrap them in `useMemo`
 * to only recalculate when the dependencies (usually props or state) change.
 * `useMemo` returns the memoized result (a value like a number, object, or string), 
  whereas `useCallback` memoizes a function.
 * Example:
```js
import React, { useState, useMemo } from 'react';

function ExpensiveCalculation({ num }) {
  const computeFactorial = (n) => {
    console.log('Calculating factorial...');
    return n <= 1 ? 1 : n * computeFactorial(n - 1);
  };

  const factorial = useMemo(() => computeFactorial(num), [num]);

  return <div>Factorial of {num} is {factorial}</div>;
}

function ParentComponent() {
  const [num, setNum] = useState(5);
  const [parentState, setParentState] = useState(0);

  return (
    <div>
      <button onClick={() => setParentState(prev => prev + 1)}>
        Increment Parent State
      </button>
      <input 
        type="number" 
        value={num} 
        onChange={(e) => setNum(Number(e.target.value))} 
      />
      <ExpensiveCalculation num={num} />
    </div>
  );
}

export default ParentComponent;
```

 * In this example, `useMemo` is used to memoize the result of the factorial computation.
 * Even if the parent component re-renders (e.g., when `parentState` changes), the factorial
 is only recalculated when the `num` value changes.

