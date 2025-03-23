[Go back](../Index.md)

# Currying in JavaScript

## What is Currying?
Currying is a functional programming technique where a function is transformed into a sequence of functions, each taking a single argument. It helps in code reusability and avoids passing the same variables multiple times.

## Syntax & Example
```javascript
function curry(fn) {
    return function curried(...args) {
        if (args.length >= fn.length) {
            return fn.apply(this, args);
        } else {
            return function (...nextArgs) {
                return curried.apply(this, args.concat(nextArgs));
            };
        }
    };
}

function sum(a, b, c) {
    return a + b + c;
}

const curriedSum = curry(sum);
console.log(curriedSum(1)(2)(3)); // Output: 6
```

## Advantages of Currying
| Feature | Benefit |
|---------|---------|
| Code Reusability | Allows partial application of functions |
| Avoids Code Duplication | Eliminates redundant arguments |
| Improves Readability | More declarative and modular code |

## Interview Questions & Answers

### **Q1: What is currying in JavaScript?**
**A:** Currying is a technique where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument.

### **Q2: How does currying help in JavaScript?**
**A:** It enhances code reusability, improves readability, and allows partial application of functions.

### **Q3: How is currying different from partial application?**
**A:** Currying always returns a sequence of functions with one argument at a time, whereas partial application returns a function with a fixed number of arguments.

### **Q4: Can you implement a simple curried function?**
```javascript
const multiply = (a) => (b) => a * b;
console.log(multiply(2)(3)); // Output: 6
```

## Summary
- Currying transforms functions to take one argument at a time.
- It enhances reusability, readability, and modularity.
- Used frequently in functional programming and higher-order functions.

