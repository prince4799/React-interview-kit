[Go back](../Index.md)

# Temporal Dead Zone (TDZ)

The **Temporal Dead Zone** is the time between the hoisting of a variable with `let` or `const` and its initialization.

## Example
```js
console.log(a);  // ❌ ReferenceError
let a = 5;
```

## Why Does This Happen?
- The variable `a` is **hoisted**, but it stays in the **TDZ** until it's initialized.
- Accessing it before initialization causes a **ReferenceError**.

---

