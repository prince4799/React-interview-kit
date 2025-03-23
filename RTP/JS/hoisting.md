[Go back](../Index.md)

# Hoisting

Hoisting is JavaScript’s default behavior of moving variable and function declarations to the top of their scope **before code execution**.

## Hoisting with `var`
```js
console.log(a); // undefined
var a = 10;
```
Even though `a` is declared after the `console.log`, it's **hoisted** to the top with a default value of `undefined`.

## Hoisting with `let` and `const`
Unlike `var`, **let** and **const** are hoisted but remain in a **Temporal Dead Zone (TDZ)** until they are assigned a value.
```js
console.log(b); // ❌ ReferenceError
let b = 20;
```

## Hoisting with Functions
```js
sayHello(); // ✅ Works due to hoisting

function sayHello() {
  console.log("Hello!");
}
```
Function **declarations** are hoisted **with their definitions**, so they can be called before they appear in the code.

---

