<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Custom Hooks → When and why to create them.</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>
Custom Hooks in React allow you to extract reusable logic from components, making code cleaner, modular, and maintainable. They are regular JavaScript functions that follow the React Hook rules and can use other hooks like useState, useEffect, etc.

## **When to Create Custom Hooks?**
* You are repeating the same logic in multiple components.
* A component’s logic becomes too complex and needs separation.
* Side effects and state management need to be reused efficiently.
* You want better code organization by encapsulating logic.

## **Why Use Custom Hooks?**
* `Code Reusability` – Write once, use multiple times.
* `Better Readability` – Improves structure by separating concerns.
* `Easy Testing` – Logic is independent of UI rendering.
* `Separation of Concerns` – UI and business logic are separated.
* `Reduces Component Re-Renders` – Helps with performance optimization.

| Feature              | Custom Hooks in React |
|----------------------|----------------------|
| Purpose             | Reuse stateful logic across components. |
| Naming Convention   | Always starts with `use` (e.g., `useFetch`, `useLocalStorage`). |
| Can Use Other Hooks? | Yes, can use `useState`, `useEffect`, etc. |
| When to Use?        | Repeated logic (API calls, local storage, etc.). |
| Benefits           | Code reuse, better readability, optimized performance. |
| Example Hooks      | `useFetch`, `useLocalStorage`, `useOnlineStatus`. |

## **How to Create a Custom Hook?**
* Example 1: useLocalStorage (Persist Data in Local Storage)
``` js
import { useState, useEffect } from "react";

function useLocalStorage(key, initialValue) {
  const [value, setValue] = useState(() => {
    const storedValue = localStorage.getItem(key);
    return storedValue ? JSON.parse(storedValue) : initialValue;
  });

  useEffect(() => {
    localStorage.setItem(key, JSON.stringify(value));
  }, [key, value]);

  return [value, setValue];
}

// Usage in a component
function ThemeSwitcher() {
  const [theme, setTheme] = useLocalStorage("theme", "light");
  return (
    <div>
      <p>Current Theme: {theme}</p>
      <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
        Toggle Theme
      </button>
    </div>
  );
}
export default ThemeSwitcher;
```

* Example 2: useFetch (Custom Hook for Fetching Data)
```js
import { useState, useEffect } from "react";

function useFetch(url) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    let isMounted = true;
    setLoading(true);

    fetch(url)
      .then((response) => response.json())
      .then((result) => {
        if (isMounted) setData(result);
      })
      .catch((err) => {
        if (isMounted) setError(err);
      })
      .finally(() => {
        if (isMounted) setLoading(false);
      });

    return () => (isMounted = false);
  }, [url]);

  return { data, loading, error };
}
// Usage in a component
function UserList() {
  const { data, loading, error } = useFetch("https://jsonplaceholder.typicode.com/users");

  if (loading) return <p>Loading...</p>;
  if (error) return <p>Error fetching data</p>;
  return (
    <ul>
      {data.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
export default UserList;
```
 
* Example 3: useOnlineStatus (Check if User is Online)
```js
import { useState, useEffect } from "react";
function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(navigator.onLine);
  useEffect(() => {
    const updateStatus = () => setIsOnline(navigator.onLine);
    window.addEventListener("online", updateStatus);
    window.addEventListener("offline", updateStatus);
    return () => {
      window.removeEventListener("online", updateStatus);
      window.removeEventListener("offline", updateStatus);
    };
  }, []);
  return isOnline;
}
// Usage in a component
function StatusIndicator() {
  const isOnline = useOnlineStatus();

  return <p>{isOnline ? "✅ Online" : "❌ Offline"}</p>;
}
export default StatusIndicator;
```

## **Common Interview Questions on Custom Hooks**
1. **What is a custom hook in React?**
A custom hook is a JavaScript function that starts with use (e.g., useFetch, useLocalStorage) and allows you to reuse stateful logic across multiple components. It can use built-in hooks like useState, useEffect, useMemo, etc.
`Key Benefit: Avoids code duplication and improves readability.`

2. **Why do we need custom hooks instead of using regular functions?**
Regular functions cannot use React hooks, but custom hooks can.

✅ `Custom Hooks:`
- Can maintain state and lifecycle methods using hooks.
- Encapsulate side effects and logic cleanly.
- Improve code reusability across components.

🚫 `Regular Functions:`
- Cannot use useState, useEffect, or any other hook.
- Cannot persist state across renders.

3. **Can a custom hook use another hook inside it?**
✅ Yes! Custom hooks can use other hooks like useState, useEffect, useContext, etc.Since,Custom hooks follow the Rules of Hooks, which allowing them to call hooks inside them.

4. **How do you share stateful logic using custom hooks?**
Custom hooks return state and functions that other components can use.

5. **What are some real-world use cases for custom hooks?**
Custom hooks can be used for:
* Fetching Data → useFetch(url)
* Local Storage Management → useLocalStorage(key, value)
* Online/Offline Status → useOnlineStatus()
* Debounce Input Handling → useDebounce(value, delay)
* Form Handling → useForm(initialValues)
* Detecting Clicks Outside a Component → useClickOutside(ref)

6. **Do custom hooks re-render when state updates?**
✅ Yes, custom hooks trigger re-renders when their internal useState updates.

7. **How does dependency management work in custom hooks using useEffect?**
In useEffect, dependencies control when the effect runs.

✅ Example: Re-fetch data when url changes
```js
function useFetch(url) {
  const [data, setData] = useState(null);
  useEffect(() => {
    fetch(url).then(res => res.json()).then(setData);
  }, [url]); // Runs only when `url` changes
  return data;
}
```
  </div>