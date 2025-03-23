<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Error Boundaries in React – Complete Guide</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

  Error Boundaries in React catch JavaScript errors that occur in a component tree and prevent the entire app from crashing by displaying a fallback UI instead.
  
  ## ** Why Do We Need Error Boundaries?**

* Prevents entire application crashes due to errors in one component.
* Displays a fallback UI instead of a broken screen.
* Logs errors for debugging without breaking the app.
* Only class components can be Error Boundaries (Hooks don’t support them yet).

## **How to Create an Error Boundary?**
An Error Boundary is a class component that implements either of these lifecycle methods:
* static getDerivedStateFromError(error) → Updates state to show fallback UI.
* componentDidCatch(error, info) → Logs error details
* Example of creating Error boundary
```js
import React, { Component } from "react";

class ErrorBoundary extends Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    return { hasError: true }; // Update state to show fallback UI
  }
  componentDidCatch(error, info) {
    console.error("Error caught by boundary:", error, info); // Log error
  }
  render() {
    if (this.state.hasError) {
      return <h2>Something went wrong.</h2>;
    }
    return this.props.children;
  }
}
export default ErrorBoundary;
```
* How to use it: You wrap a component inside an Error Boundary to catch its errors.
```js
import React from "react";
import ErrorBoundary from "./ErrorBoundary"; // Import the boundary

const BuggyComponent = () => {
  throw new Error("Oops! Something went wrong.");
};

export default function App() {
  return (
    <ErrorBoundary>
      <BuggyComponent />
    </ErrorBoundary>
  );
}
```

## **When to Use Error Boundaries?**
 * Wrapping entire app to catch all errors
 ```js
 <ErrorBoundary>
  <App />
</ErrorBoundary>
 ```
 * Only around specific components:
```js
<ErrorBoundary>
  <ProfileComponent />
</ErrorBoundary>
```
* Around third-party libraries:
```js
<ErrorBoundary>
  <ThirdPartyChart />
</ErrorBoundary>
```

## **Can Hooks Be Used as Error Boundaries?**
❌ No, React Hooks (like useEffect) cannot catch errors in rendering.
✅ Instead, wrap functional components inside Error Boundary class components.

## **Interview Questions & Answers**
 ### **Basic Questions**

**What is an Error Boundary in React?**
* A React class component that catches JavaScript errors and prevents app crashes.

**How do Error Boundaries work?**
* They use getDerivedStateFromError to update UI and componentDidCatch to log errors.

**Can we use Error Boundaries in functional components?**
* No, Error Boundaries only work in class components.

**Where should we use Error Boundaries?**
* Around the whole app, third-party libraries, or any component that might break.

### **Advanced Questions**
**What’s the difference between try/catch and Error Boundaries?**
* try/catch only works for event handlers, while Error Boundaries catch rendering errors.

**Can Error Boundaries catch all errors?**
❌No, they cannot catch:
- Errors in event handlers
- Errors in async functions
- Errors in server-side rendering (SSR)
**How do you handle errors in React functional components?**
* Use Error Boundaries or ErrorBoundary wrappers.



  </div>