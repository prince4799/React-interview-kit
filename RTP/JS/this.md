[Go back](../Index.md)


# **Understanding the `this` Keyword in JavaScript**

The `this` keyword in JavaScript refers to the object that is executing the current function. Its value depends on how and where it is used.

## **1. How `this` Works in Different Contexts**

### **1.1 Global Context**
In the global execution context (outside any function), `this` refers to the global object.

```javascript
console.log(this); // In a browser, this refers to `window`
```

### **1.2 Inside a Function**
In non-strict mode, `this` inside a function refers to the global object (`window` in browsers). In strict mode, it is `undefined`.

```javascript
function showThis() {
    console.log(this); // In non-strict mode: window, in strict mode: undefined
}
showThis();
```

### **1.3 Inside an Object Method**
When a function is a method of an object, `this` refers to the object.

```javascript
const obj = {
    name: "JavaScript",
    getName: function () {
        console.log(this.name); // Refers to obj
    }
};
obj.getName(); // JavaScript
```

### **1.4 In Constructor Functions**
When using a constructor function, `this` refers to the new object being created.

```javascript
function Person(name) {
    this.name = name;
}
const person1 = new Person("John");
console.log(person1.name); // John
```

### **1.5 Arrow Functions and `this`**
Arrow functions do not have their own `this`. Instead, they inherit `this` from their lexical scope.

```javascript
const obj2 = {
    name: "ES6",
    getName: () => {
        console.log(this.name); // `this` is inherited from the outer scope (window in global scope)
    }
};
obj2.getName(); // Undefined
```

### **1.6 `this` in Event Listeners**
In an event listener, `this` refers to the element that received the event.

```javascript
document.getElementById("btn").addEventListener("click", function () {
    console.log(this); // Refers to the button element
});
```

## **2. Changing the Value of `this`**

| Method | Description |
|--------|-------------|
| `call()` | Calls a function with a specified `this` value and arguments |
| `apply()` | Similar to `call()`, but arguments are passed as an array |
| `bind()` | Returns a new function with `this` bound to a specified object |

### **2.1 Using `call()`**
```javascript
const person = { name: "Alice" };
function greet() {
    console.log("Hello, " + this.name);
}
greet.call(person); // Hello, Alice
```

### **2.2 Using `apply()`**
```javascript
function introduce(age, profession) {
    console.log(`${this.name} is a ${age}-year-old ${profession}.`);
}
introduce.apply(person, [25, "Developer"]); // Alice is a 25-year-old Developer.
```

### **2.3 Using `bind()`**
```javascript
const boundFunction = greet.bind(person);
boundFunction(); // Hello, Alice
```

## **3. Interview Questions & Answers**

### **Q1: What is `this` in JavaScript?**
**A:** `this` refers to the object that is executing the function. Its value depends on how the function is called.

### **Q2: How does `this` behave in arrow functions?**
**A:** Arrow functions do not have their own `this`; they inherit `this` from their surrounding lexical scope.

### **Q3: What happens when using `this` inside an event listener?**
**A:** Inside an event listener, `this` refers to the element that triggered the event.

### **Q4: How can we explicitly change the value of `this`?**
**A:** We can use `call()`, `apply()`, or `bind()` to change the value of `this` explicitly.

### **Q5: What is the difference between `call()`, `apply()`, and `bind()`?**
| Method | Execution | Arguments |
|--------|------------|------------|
| `call()` | Executes the function immediately | Arguments are passed individually |
| `apply()` | Executes the function immediately | Arguments are passed as an array |
| `bind()` | Returns a new function with `this` bound | Arguments are passed individually |

