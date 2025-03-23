  [⬅ Go Back](../Index.md) 
   <h1 style="text-align: center; margin: 0; color:#00fc04; ">Why do we use contextAPI?</h1>

 ### ``The purpose of context api are :``

 - ``Not to make rendering more performant`` 
 - But to make ``cleaner syntax``.
 - Since the context API ``doesn't prevent the rendering`` of the middle component hence
   it doesn't make our app more performant.
 - To ``get rid of prop drilling``.
 - ![Screenshot](../definitions/Screenshot%202024-09-29%20at%207.43.39%20PM.png)


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
