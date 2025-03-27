[Go back](../Index.md)

# ES6 Features

ECMAScript 6 (ES6) introduced several improvements to JavaScript. Here are some key features:

## 1. Let & Const
- `let` allows block-scoped variables.
- `const` is used for constants that cannot be reassigned.

```js
let name = "John";
const age = 25;
```

## 2. Arrow Functions
- Shorter syntax for functions.
- Lexical `this` binding.

```js
const add = (a, b) => a + b;
```

## 3. Template Literals
- Allows multi-line strings and string interpolation.

```js
const message = `Hello, my name is ${name}`;
```

## 4. Destructuring
- Extract values from arrays and objects easily.

```js
const [a, b] = [1, 2];
const { name, age } = { name: "John", age: 25 };
```

## 5. Spread & Rest Operators
- `...` is used to expand or collect elements.

```js
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5];
const sum = (...nums) => nums.reduce((a, b) => a + b);
```

## 6. Default Parameters
- Set default values for function parameters.

```js
const greet = (name = "Guest") => `Hello, ${name}`;
```

## 7. Classes
- Simplifies object-oriented programming in JavaScript.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    return `Hello, my name is ${this.name}`;
  }
}
```

## 8. Promises
- Handles asynchronous operations.

```js
const fetchData = () => new Promise(resolve => setTimeout(() => resolve("Data fetched"), 1000));
```

## 9. Modules (Import & Export)
- Enables modular JavaScript.

```js
// module.js
export const hello = () => "Hello!";
// main.js
import { hello } from "./module.js";
console.log(hello());
```

## Comparison Table

| Feature          | ES5 Approach | ES6 Approach |
|-----------------|-------------|-------------|
| Variable Declaration | `var` | `let`, `const` |
| Function Syntax | `function() {}` | `() => {}` |
| String Concatenation | `"Hello" + name` | `` `Hello ${name}` `` |
| Object Methods | `obj.method = function() {}` | `method() {}` |

## Interview Questions

### 1. What is the difference between `let`, `const`, and `var`?
**Answer:** `var` is function-scoped, `let` is block-scoped, and `const` is also block-scoped but cannot be reassigned.

### 2. How does an arrow function differ from a regular function?
**Answer:** Arrow functions do not have their own `this` and inherit `this` from the surrounding scope.

### 3. What is the use of the spread operator (`...`)?
**Answer:** It allows expanding iterable elements in places where multiple arguments or elements are expected.

 **You should also visit [here](https://www.w3schools.com/react/react_es6.asp) for more details**

