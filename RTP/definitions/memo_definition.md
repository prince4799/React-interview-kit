
  [⬅ Go Back](../Index.md) 
   <h1 style="text-align: center; margin: 0; color:#00fc04; ">What is React.memo in React?</h1>

 * In React, if the parent component re-renders, its children also re-render by default, even if the props of the child have not changed. 
 * To prevent unnecessary re-renders of the child component, we can wrap the child component  with `React.memo`. This ensures that the child component will only re-render when its props have changed.
 * In other words,```React.memo optimizes performance by skipping re-rendering  of a component if its props remain the same.```
 * Example:
 
```js
import React, { useState } from 'react';

const ChildComponent = React.memo(({ name }) => {
  console.log('Child rendered');
  return <div>Child component: {name}</div>;
});

function ParentComponent() {
  const [parentState, setParentState] = useState(0);
  const [name, setName] = useState('React');

  return (
    <div>
      <button onClick={() => setParentState(prev => prev + 1)}>
        Increment Parent State
      </button>
      <button onClick={() => setName('React Memo')}>
        Change Name
      </button>
      <ChildComponent name={name} />
    </div>
  );
}

export default ParentComponent;
```

 * In this example, `ChildComponent` is wrapped in `React.memo`. It only re-renders when 
 * the `name` prop changes. If you click the "Increment Parent State" button, the parent
 * re-renders, but the `ChildComponent` doesn't re-render unless the `name` changes.

