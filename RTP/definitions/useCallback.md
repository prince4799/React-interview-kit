  [⬅ Go Back](../Index.md) 
   <h1 style="text-align: center; margin: 0; color:#00fc04; ">What is useCallback in React?</h1>

 * In JavaScript, functions are reference types, meaning that even if two functions 
  have the same implementation, they will be treated as different due to 
  referential inequality (e.g., `functionA !== functionB` even if they do the same thing).
 * This causes components to re-render because the function passed as a prop is considered "new" 
  every time the parent re-renders. To prevent this, we use `useCallback`, which memoizes 
  the function so that it doesn't get recreated unless its dependencies change.
 * `useCallback` returns a memoized function, whereas `useMemo` returns a memoized value.
 * Example:

```js
import React, { useState, useCallback } from 'react';

const ChildComponent = React.memo(({ fetchData }) => {
  console.log('Child rendered');
  return <button onClick={fetchData}>Fetch Data</button>;
});

function ParentComponent() {
  const [count, setCount] = useState(0);

  const fetchData = useCallback(() => {
    console.log('Fetching data...');
  }, []);

  return (
    <div>
      <button onClick={() => setCount(prev => prev + 1)}>
        Increment Parent State
      </button>
      <ChildComponent fetchData={fetchData} />
    </div>
  );
}

export default ParentComponent;
```

 * In this example, the `fetchData` function is memoized using `useCallback`. 
 * Without `useCallback`, the `ChildComponent` would re-render every time the parent component
 re-renders (due to referential inequality). However, with `useCallback`, `fetchData` 
 is the same function reference between renders, preventing unnecessary re-renders of the child.

