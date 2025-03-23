[Go back](../Index.md)


# Call, Bind, and Apply in JavaScript

## **1. Call, Bind, and Apply - Overview**
These methods are used to control the value of `this` when invoking functions.

| Method | Returns | Execution | Arguments | Use Case |
|--------|---------|------------|------------|----------|
| `call()`  | Immediate | Yes | Comma-separated | Invokes function with specified `this` value & arguments |
| `apply()` | Immediate | Yes | Array format | Similar to `call`, but takes arguments as an array |
| `bind()`  | New function | No | Comma-separated | Returns a new function with specified `this` value |

---
## **2. Call Method**
- Calls a function with a specified `this` value and arguments provided separately.

### **Example:**
```js
function greet(greeting, punctuation) {
    console.log(greeting + ' ' + this.name + punctuation);
}
const person = { name: 'Alice' };
greet.call(person, 'Hello', '!'); // Hello Alice!
```

---
## **3. Apply Method**
- Similar to `call()`, but takes arguments as an array.

### **Example:**
```js
greet.apply(person, ['Hi', '!!']); // Hi Alice!!
```

---
## **4. Bind Method**
- Returns a new function with `this` bound to the provided object.

### **Example:**
```js
const boundGreet = greet.bind(person, 'Hey');
boundGreet('!'); // Hey Alice!
```

---
## **5. Common Interview Questions with Answers**

### **Q1: What is the difference between `call`, `apply`, and `bind`?**
| Feature | `call()` | `apply()` | `bind()` |
|---------|---------|---------|---------|
| Execution | Immediate | Immediate | Returns new function |
| Arguments | Comma-separated | Array | Comma-separated |
| Modifies `this`? | Yes | Yes | Yes |

### **Q2: When should you use `bind()` instead of `call()`?**
**Answer:** Use `bind()` when you need a function with a preset `this` value for later execution, whereas `call()` is used when you need immediate execution.

### **Q3: Can you pass arguments after using `bind()`?**
**Answer:** Yes, `bind()` supports both pre-set and later-passed arguments.
```js
const boundGreet = greet.bind(person, 'Good morning');
boundGreet('?'); // Good morning Alice?
```

### **Q4: Which method is best suited for borrowing functions from another object?**
**Answer:** `call()` or `apply()` are best suited for function borrowing.
```js
const person2 = { name: 'Bob' };
greet.call(person2, 'Hi', '!'); // Hi Bob!
```

