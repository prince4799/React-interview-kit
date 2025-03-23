[Go back](../Index.md)

# Objects & Types of Operations

## Introduction to Objects in JavaScript
JavaScript objects are collections of key-value pairs, where the keys are strings (or Symbols) and the values can be of any type. Objects allow us to store, retrieve, and manipulate structured data efficiently.

## Creating Objects
### 1. Object Literals
```javascript
const person = {
    name: "John",
    age: 30,
    greet: function() {
        console.log("Hello, " + this.name);
    }
};
```

### 2. Using `new Object()`
```javascript
const person = new Object();
person.name = "John";
person.age = 30;
```

### 3. Using Object.create()
```javascript
const personPrototype = {
    greet: function() {
        console.log("Hello, " + this.name);
    }
};
const person = Object.create(personPrototype);
person.name = "John";
```

### 4. Using Classes (ES6)
```javascript
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    greet() {
        console.log("Hello, " + this.name);
    }
}
const person = new Person("John", 30);
```

## Common Object Operations

### 1. Adding Properties
```javascript
person.job = "Engineer";
```

### 2. Removing Properties
```javascript
delete person.age;
```

### 3. Checking Property Existence
```javascript
console.log("name" in person); // true
console.log(person.hasOwnProperty("age")); // false
```

### 4. Iterating Over Object Properties
```javascript
// Using for...in
for (let key in person) {
    console.log(key, person[key]);
}
```

### 5. Object.keys(), Object.values(), and Object.entries()
```javascript
console.log(Object.keys(person)); // ["name", "job"]
console.log(Object.values(person)); // ["John", "Engineer"]
console.log(Object.entries(person)); // [["name", "John"], ["job", "Engineer"]]
```

### 6. Object.assign()
```javascript
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = Object.assign({}, obj1, obj2);
console.log(merged); // { a: 1, b: 2 }
```

### 7. Object Spread Operator (ES6)
```javascript
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 };
console.log(merged); // { a: 1, b: 2 }
```

### 8. Object.freeze() & Object.seal()
```javascript
const obj = { name: "John" };
Object.freeze(obj);
obj.name = "Doe"; // Won't change

const obj2 = { age: 30 };
Object.seal(obj2);
obj2.age = 35; // Allowed
```

## Most Asked Interview Questions

### 1. What are objects in JavaScript?
Objects in JavaScript are key-value pairs that store multiple properties and methods.

### 2. How do you iterate over object properties?
Using `for...in`, `Object.keys()`, `Object.values()`, or `Object.entries()`.

### 3. What is the difference between `Object.freeze()` and `Object.seal()`?
- `Object.freeze()` prevents modification and addition of properties.
- `Object.seal()` prevents adding/removing properties but allows modifications to existing ones.

### 4. How can you clone an object in JavaScript?
Using `Object.assign()`, spread operator (`{ ...obj }`), or `JSON.parse(JSON.stringify(obj))`.

### 5. How are objects passed in JavaScript (by value or by reference)?
Objects are passed by reference, meaning changes to an object inside a function affect the original object.

### 6. How can you check if an object has a specific property?
Using `in` operator (`"key" in obj`) or `hasOwnProperty()` (`obj.hasOwnProperty("key")`).

### 7. What is the difference between `Object.create()` and class-based objects?
- `Object.create()` creates an object with a specified prototype.
- ES6 classes provide a more structured and reusable approach.

### 8. What is prototype chaining in JavaScript?
Prototype chaining allows objects to inherit properties and methods from their prototypes, forming a chain-like structure.

### 9. How do you merge two objects in JavaScript?
Using `Object.assign()` or spread syntax (`{ ...obj1, ...obj2 }`).

### 10. What is the difference between shallow and deep copy of objects?
- **Shallow Copy:** Copies references to nested objects (`Object.assign()`, `{ ...obj }`).
- **Deep Copy:** Recursively copies all properties (`JSON.parse(JSON.stringify(obj))`, `structuredClone(obj)`).


