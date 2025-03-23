<div style="background-color:rgb(0, 0, 0); padding: 10px; flex:1; height:100%; width:100%"> 

  [⬅ Go Back](./Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">Prop drilling and other concepts</h1>
  <div style="height: 5px; width: 100%; background-color: #000; display: block; margin-top: 5px;"></div>

## **What is Prop Drilling**

Prop Drilling is when you pass props through multiple layers of components, even if intermediate components don’t use them, just to get the data to a deeply nested child.

### **Why is Prop Drilling a Problem?**
- `Unnecessary prop passing:` Components that don’t need the prop still receive it.
- `Code maintenance issues:` If prop structure changes, multiple components need updates.
- ` Reduces reusability:` Components become tightly coupled.
- `Problem:` If there were multiple levels (e.g., Grandparent -> Parent -> Child), every component in between would need to pass username, even if it doesn't use it.

### **Ways to avoid Prop drilling.**

- Use [Context API](#context-api-best-for-global-state) for small apps.
- Use [State Management Liabraries](#state-management-libraries-redux-zustand-recoil)(Redux/Zustand/Recoil) for large-scale apps.
- Use [Composition Pattern](#composition-pattern-pass-components-instead-of-data) when passing components makes sense.

## **Context API (Best for Global State)**
 Instead of passing props through multiple layers, store them in a React Context.
```js
import React, { createContext, useContext } from "react";
const UserContext = createContext();
function Child() {
  const username = useContext(UserContext); // Accessing context
  return <h3>Welcome, {username}!</h3>;
}
function Parent() {
  return <Child />;
}
function App() {
  return (
    <UserContext.Provider value="JohnDoe">
      <Parent />
    </UserContext.Provider>
  );
}
export default App;
```

##  **State Management Libraries (Redux, Zustand, Recoil)**
If data needs to be shared across many components, use Redux, Zustand, or Recoil.
Example with Redux:
```js
import { Provider, useSelector } from "react-redux";
import { createStore } from "redux";
const reducer = (state = { username: "JohnDoe" }) => state;
const store = createStore(reducer);
function Child() {
  const username = useSelector((state) => state.username);
  return <h3>Welcome, {username}!</h3>;
}
function App() {
  return (
    <Provider store={store}>
      <Child />
    </Provider>
  );
}
export default App;
```
##  **Composition Pattern (Pass Components Instead of Data)**
Instead of prop drilling, pass components as children.
```js
function Wrapper({ children }) {
  return <div>{children}</div>;
}
function App() {
  return (
    <Wrapper>
      <h3>Welcome, JohnDoe!</h3>
    </Wrapper>
  );
}
export default App;
```

## **Major Difference Between Context API and Other State Management Libraries (Redux, Zustand, Recoil, etc.)**

| Feature            | React Context API                        | Redux                                      | Zustand                                | Recoil                                    |
|--------------------|---------------------------------------|-------------------------------------------|---------------------------------------|------------------------------------------|
| **Purpose**       | Share global state across components | Centralized state management for large applications | Simple and lightweight state management | Atomic state management with better reactivity |
| **Complexity**    | Simple                                | Complex (requires reducers, actions)     | Very simple (store-based)            | Moderate (declarative state using atoms) |
| **Boilerplate**   | Minimal                               | High                                      | Very low                             | Low                                      |
| **Performance**   | Can cause unnecessary re-renders     | Optimized with selectors and middlewares | Fast, uses direct store updates      | Efficient re-renders using atoms        |
| **Best For**      | Small to medium apps                 | Large-scale apps with complex state      | Small to large apps needing minimal setup | Apps needing fine-grained reactivity   |
| **Async Handling**| Use `useEffect` or external libraries | Middleware like Thunk/Saga               | Built-in async handling              | Built-in async (async selectors)       |
| **DevTools**      | No built-in DevTools                 | Powerful Redux DevTools                  | Basic DevTools                       | Good debugging tools                   |
| **Ease of Learning** | Easy                              | Steep learning curve                     | Very easy                            | Moderate                                |

  </div>