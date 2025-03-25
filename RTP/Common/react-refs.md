<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">React Refs – Complete Guide</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>
React Refs provide a way to directly access DOM elements or React components. They are mainly used when you need imperative control over an element, such as managing focus, text selection, or triggering animations.
 
 ## **Why Use Refs?**
- Accessing DOM elements directly (e.g., focusing an input field).
- Storing values persistently without causing re-renders.
- Interacting with third-party libraries (e.g., handling animations with GSAP).
- Managing uncontrolled components (e.g., file uploads).

| When to Use Refs? | ❌ When NOT to Use Refs? |
|-------------------|------------------------|
| 🔹 Managing focus, animations, or selecting text | 🚫 For normal state updates (use `useState` instead). |
| 🔹 Accessing child DOM elements | 🚫 For passing data between components (use `props` or `context`). |
| 🔹 Storing values that don’t trigger re-renders | |

| ❌ Avoid `useRef` When...                    | ✅ Use `useRef` When...                        |
|----------------------------------------------|-----------------------------------------------|
| You need to trigger UI updates              | You need a reference to a DOM element        |
| You are storing values that should re-render | You want to persist values across renders **without** re-rendering |
| Managing state (use `useState` instead)      | Storing timers, intervals, or previous values |
| Handling form inputs (use `useState`)        | Avoiding re-renders with stable references   |
| Using it inside event handlers (can be stale)| Storing mutable values outside of reactivity |


 ## **How to Create and Use Refs?**
`Refs in React are created using the useRef() hook in functional components or React.createRef() in class components`.
```js
import React, { useRef } from "react";
const InputFocus = () => {
  const inputRef = useRef(null); // Create a ref
  const handleFocus = () => {
    inputRef.current.focus(); // Directly access input DOM element
  };
  return (
    <div>
      <input ref={inputRef} type="text" placeholder="Type here..." />
      <button onClick={handleFocus}>Focus Input</button>
    </div>
  );
};
export default InputFocus;
```
## **Forwarding Refs to Child Components**
* By default, refs do not pass down to child components. To enable this, we use React.forwardRef.
* Example: Forwarding a Ref to a Child Component
```js
import React, { forwardRef, useRef } from "react";
// Child component with forwarded ref
const InputComponent = forwardRef((props, ref) => (
  <input ref={ref} type="text" {...props} />
));
const ParentComponent = () => {
  const inputRef = useRef(null);
  return (
    <div>
      <InputComponent ref={inputRef} placeholder="Forwarded Ref Example" />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
};
export default ParentComponent;
```
## **Storing Mutable Values with useRef() (Does Not Cause Re-Renders)**
- Unlike useState, updating a useRef value does not trigger a re-render.

- Example: Storing Mutable Values Without Re-Rendering
```js
import React, { useRef, useState } from "react";
const Counter = () => {
  const countRef = useRef(0);
  const [renderCount, setRenderCount] = useState(0);
  const increment = () => {
    countRef.current += 1; // Updates ref value
    console.log("Ref Value:", countRef.current);
  };
  return (
    <div>
      <p>Render Count: {renderCount}</p>
      <button onClick={increment}>Increase Ref (No Re-render)</button>
      <button onClick={() => setRenderCount(prev => prev + 1)}>Trigger Re-render</button>
    </div>
  );
};
export default Counter;
```
## **Refs in Uncontrolled Components**
- Refs help handle form inputs where React does not control the state.
- Example: Getting Input Value Without useState
```js
import React, { useRef } from "react";
const UncontrolledForm = () => {
  const inputRef = useRef(null);
  const handleSubmit = (e) => {
    e.preventDefault();
    alert(`Entered Value: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input ref={inputRef} type="text" placeholder="Enter text" />
      <button type="submit">Submit</button>
    </form>
  );
};
export default UncontrolledForm;
```
## **Interview Questions & Answers**

### **Basic Questions**
### **What is useRef used for?**
- useRef is used to access DOM elements and store values that don’t trigger re-renders.

### **What is the difference between useRef and useState?**
- useState causes re-renders when updated, while useRef does not.

### **What is React.forwardRef?**
- It allows passing refs to child components.

### **Can we use useRef to store values between renders?**
- Yes, but updating useRef won’t trigger a re-render.

### **Advanced Questions**
### **What is the difference between controlled and uncontrolled components?**
- Controlled components store input state in React (useState).
- Uncontrolled components use ref to read values directly from the DOM.

### **How do refs improve performance in React?**
- They avoid unnecessary re-renders by storing values outside React’s render cycle.

### **When should you use useRef instead of useState?**
- When you need to store values without triggering re-renders.
  </div>
