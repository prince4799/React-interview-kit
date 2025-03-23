
  [⬅ Go Back](../Index.md) 
 <h1 style="text-align: center; margin: 0; color:#00fc04; ">What is useState in React?</h1>
 
 
useState is a React Hook that allows functional components to have state. It helps manage dynamic values and re-renders the component when the state changes.

`useState hook doesn't update the value of the state immediately it takes some time so in below:
`count` will be 1 on single click of the button`

```js
import React from 'react'
function ToDo() {
    const [count,setCount]=useState(0)
  return (
    <div>
        <h1>{count}</h1> 
        <button onClick={(e)=>{
           setCount(count+1)  // 0+1
           setCount(count+1)  // 0+1
              
        }}>increment</button>
    </div>
  )
}

export default ToDo
```

but if you want to achieve it then do it like below

```js
function ToDo() {

    const [count,setCount]=useState(0)
  return (
    <div>
        <h1>{count}</h1> 
        <button onClick={(e)=>{
           setCount((prev)=>prev+1)  // 0+1
           setCount((prev)=>prev+1)  // 1+1
              
        }}>increment</button>
    </div>
  )
}
```