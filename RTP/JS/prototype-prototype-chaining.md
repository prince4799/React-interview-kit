[Go back](../Index.md)

# Prototype & Prototype Chaining

## 1. What is Prototype in JavaScript?
- In JavaScript, every function and object has a `prototype` property.
- It acts as a blueprint for creating new objects.
- Used to enable inheritance in JavaScript.

### Example:
```js
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log(`Hello, my name is ${this.name}`);
};

const person1 = new Person("Alice");
person1.greet(); // Output: Hello, my name is Alice
```

## 2. What is Prototype Chaining?
- When accessing a property on an object, JavaScript first looks for it on the object itself.
- If not found, it checks the object's prototype, then its prototype, and so on.
- This chain continues until it reaches `null`.

### Example:
```js
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function() {
  console.log(`${this.name} makes a sound`);
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

// Inheriting from Animal
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

const dog1 = new Dog("Buddy", "Golden Retriever");
dog1.speak(); // Output: Buddy makes a sound
```

## 3. Prototype vs. `__proto__`
| Feature | Prototype (`prototype`) | `__proto__` |
|---------|----------------|------------|
| What is it? | Property of constructor functions | Reference to an object's prototype |
| Used for? | Defining methods for objects created from the constructor | Accessing the prototype chain |
| Modifiable? | Yes | Yes (not recommended) |

---

## \ud83d\udccc **Common Interview Questions**
### 1. What is the difference between `prototype` and `__proto__`?
- `prototype` is a property of constructor functions that defines methods for new objects.
- `__proto__` is a reference that links an object to its prototype.

### 2. How does prototype chaining work?
- If an object doesn’t have a property, JavaScript looks up its prototype chain.
- The process continues until it reaches `null`.

### 3. How can you implement inheritance using prototype?
- Use `Object.create()` or manually set the prototype with `Object.setPrototypeOf()`.

```js
const parent = { greet: function() { console.log("Hello!"); } };
const child = Object.create(parent);
child.greet(); // Output: Hello!
```

