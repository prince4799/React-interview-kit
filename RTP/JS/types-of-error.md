[Go back](../Index.md)

# Types of Errors

JavaScript has three main types of errors:

## 1️⃣ SyntaxError
Occurs when the code has incorrect syntax.
```js
let a = ;  // ❌ SyntaxError: Unexpected token ';'
```

## 2️⃣ ReferenceError
Occurs when trying to access an undeclared variable.
```js
console.log(x);  // ❌ ReferenceError: x is not defined
```

## 3️⃣ TypeError
Occurs when an operation is performed on an invalid data type.
```js
let num = 10;
num();  // ❌ TypeError: num is not a function
```

---


