
<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

[⬅ Go Back](./components-props-state-hooks.md) 
<h1 style="text-align: center; margin: 0; color:#00fc04; ">Deep Explanation of HOC, Controlled, and Uncontrolled Components in React</h1>
<div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

 <h2 style=" margin: 0; color:#57acf2; ">Higher-Order Components (HOC) in React</h2>

`A Higher-Order Component (HOC) is a function that takes a component as input and returns a new component with enhanced behavior. HOCs allow code reuse, logic abstraction, and component modification without modifying the original component.`

### **Key Features of HOC:**
- Used for code reuse across multiple components.
- Encapsulates logic like authentication, logging, and data fetching.
- Does not modify the original component; instead, it wraps it.
- There is and alternative for the HOCs```Render Props``
- Below is the examle of it :Here, withLoading is an HOC that adds a loading spinner to any component that needs it.
```js
import React from "react";
// Higher-Order Component that adds a loading spinner
function withLoading(Component) {
  return function EnhancedComponent({ isLoading, ...props }) {
    if (isLoading) return <h2>Loading...</h2>;
    return <Component {...props} />;
  };
}

// Regular component
function DataDisplay({ data }) {
  return <h3>Data: {data}</h3>;
}

// Using HOC to wrap the component
const DataWithLoading = withLoading(DataDisplay);
export default function App() {
  return <DataWithLoading isLoading={false} data="Hello World!" />;
}
```

### **When to Use HOC?**
- When multiple components need the same logic (e.g., authentication, permissions).
- For data fetching, error handling, or logging.
- When following the DRY (Don't Repeat Yourself) principle.

 <h2 style=" margin: 0; color:#57acf2; ">Controlled Components in React</h2>

A Controlled Component is a component where React fully controls the form elements (like `<input>`, `<textarea>`, `<select>`) by storing their values in the state.

### **Key Features of Controlled Components:**
- Form elements do not store their own state, React manages it.
- The useState hook controls the input value.
- Changes in the input field trigger onChange events, updating the state.
- Below is the eg of it: Here, value={name} ensures React controls the input field.
```js
import React, { useState } from "react";
function ControlledForm() {
  const [name, setName] = useState("");
  return (
    <div>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>Typed Name: {name}</p>
    </div>
  );
}
export default ControlledForm;
```
 ### **When to Use Controlled Components?**
- When you need real-time validation or instant UI updates.
- When form data must be manipulated before submission.
- When integrating with state management (Redux, Context API).

<h2 style=" margin: 0; color:#57acf2; ">Uncontrolled Components in React</h2>

An Uncontrolled Component is a component where the form elements store their own state, and React does not directly control them. Instead, React accesses values using useRef.

### **Key Features of Uncontrolled Components:**
- The DOM controls the input value, not React.
- Uses useRef to read values instead of useState.
- Useful when dealing with large forms where React's state management might slow down performance.
- Below is its eg: Here, ref={inputRef} allows us to access the input value using inputRef.current.value.
```js
import React, { useRef } from "react";
function UncontrolledForm() {
  const inputRef = useRef(null);
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Entered Name: ${inputRef.current.value}`);
  };
  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">Submit</button>
    </form>
  );
}
export default UncontrolledForm;
```
### **When to Use Uncontrolled Components?**
- When dealing with third-party libraries (like file uploads).
- When working with legacy code that doesn't follow React's controlled approach.
- When performance optimization is needed, and React state is not necessary.

<h2 style=" margin: 0; color:#57acf2; ">Render Props (Alternative to HOCs)</h2>

Render Props is another way to share logic between components using a function as a child.
- Below is the example of it
```js
function MouseTracker({ render }) {
  const [x, setX] = useState(0);
  const [y, setY] = useState(0);
  return (
    <div onMouseMove={(e) => { setX(e.clientX); setY(e.clientY); }}>
      {render(x, y)}
    </div>
  );
}
function App() {
  return (
    <MouseTracker render={(x, y) => <h1>Mouse position: {x}, {y}</h1>} />
  );
}
```

</div>