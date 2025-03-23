[Go back](../Index.md)

# Call Stack

The **Call Stack** is a data structure in JavaScript that keeps track of function execution. It follows the **Last In, First Out (LIFO)** principle.

## How it Works
- When a function is called, it's **pushed** onto the stack.
- When the function completes, it's **popped** off the stack.
- If a function calls another function, the new function goes on top of the stack.

### Example
```js
function first() {
  console.log("First function");
  second();
}

function second() {
  console.log("Second function");
}

first();
```

### Execution Order
1. `first()` is pushed onto the stack.
2. `first()` calls `second()`, so `second()` is pushed.
3. `second()` runs and is popped off.
4. `first()` completes and is popped off.

---





