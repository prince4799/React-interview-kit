
  [⬅ Go Back](../Index.md) 
   <h1 style="text-align: center; margin: 0; color:#00fc04; ">What is useEffect in React?</h1>

`useEffect` is a **React Hook** that performs **side effects** in functional components.  
A **side effect** is anything that interacts **outside the component**, such as:  
- Fetching data from an API 🛰️  
- Updating the DOM 📌  
- Setting up subscriptions 🎧  
- Managing timers or intervals ⏳  

---

## **🔹 Syntax of `useEffect`**
```jsx
useEffect(callback, dependencies);
```

## **Different Cases of useEffect**
### **Running on Every Render (No Dependency Array)**
- Runs after every render (initial + updates).
- Use Case: Logging, animations, general side effects.
```js
useEffect(() => {
  console.log("Component re-rendered!");
});
```

## **Running Only Once (On Mounting)**
- Runs only on first render by passing an empty dependency array []
- Use Case: API calls, event listeners, setting up subscriptions.
```js
useEffect(() => {
  console.log("Component mounted!");
}, []);
```

## **Running When a Specific State/Prop Changes**
- Runs only when the given dependency changes.
- Use Case: Fetching new data when a value changes.
```js
useEffect(() => {
  console.log(`The count changed to: ${count}`);
}, [count]);
```
## **Cleanup Function (Component Unmounting)**
- Useful for removing event listeners, stopping timers, or cleaning memory.
- Use Case: Removing event listeners, clearing intervals.
```js
useEffect(() => {
  const interval = setInterval(() => {
    console.log("Running...");
  }, 1000);

  return () => {
    clearInterval(interval);
    console.log("Cleanup on unmount!");
  };
}, []);
```

## **Best Practices for useEffect**
* Use cleanup functions to avoid memory leaks.
* Keep dependencies optimized to avoid unnecessary re-renders.
* Prefer separate useEffect hooks for different concerns.
* Use React Query or SWR for complex data fetching instead of useEffect.

