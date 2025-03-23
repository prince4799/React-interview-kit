[Go back](../Index.md)

# Memory & Its Management

Memory management is a crucial concept in JavaScript, as it directly impacts the performance and efficiency of applications. JavaScript primarily uses two types of memory: **Stack Memory** and **Heap Memory**.

## 1. Heap Memory
Heap memory is an **unstructured memory pool** where objects, functions, and closures are stored. It is dynamically allocated and accessed by reference.

### Characteristics of Heap Memory:
- Used for storing objects and reference types.
- Dynamic memory allocation.
- Requires garbage collection for memory management.

### Example:
```js
let obj = { name: "John", age: 30 }; // Stored in heap memory
let arr = [1, 2, 3, 4]; // Arrays are also stored in the heap
```

---

## 2. Stack Memory
Stack memory is a **structured memory pool** that follows the **Last In, First Out (LIFO)** principle. It is used for **storing primitive data types** and **function execution contexts**.

### Characteristics of Stack Memory:
- Stores primitive values (e.g., numbers, strings, booleans).
- Stores function execution contexts.
- Follows a LIFO structure for memory allocation and deallocation.

### Example:
```js
function greet() {
    let name = "Alice"; // Stored in stack memory
    console.log("Hello, " + name);
}
greet();
```

---

## 3. Difference Between Stack and Heap Memory

| Feature           | Stack Memory | Heap Memory |
|------------------|-------------|-------------|
| Storage Type    | Primitive data types, function execution contexts | Objects, functions, arrays |
| Memory Access   | Fast (LIFO mechanism) | Slower (dynamic allocation) |
| Lifetime        | Short-lived | Long-lived (until garbage collection) |
| Memory Management | Automatically managed | Requires garbage collection |

---

## 4. Garbage Collection
JavaScript automatically manages memory using **garbage collection**. The **Mark-and-Sweep algorithm** is commonly used to clean up unused memory.

### Example of Memory Leak (Preventing Unused References):
```js
let user = { name: "Bob" };
user = null; // The object is now eligible for garbage collection
```

---

## 5. Important Interview Questions & Answers

### **Q1: What is the difference between Stack and Heap memory?**
**A:** Stack memory is used for storing primitive values and function calls, whereas heap memory is used for objects and reference types.

### **Q2: How does JavaScript handle memory management?**
**A:** JavaScript uses **garbage collection** with the **Mark-and-Sweep algorithm** to free unused memory.

### **Q3: What is a memory leak in JavaScript?**
**A:** A memory leak occurs when memory is allocated but never released, leading to increased memory consumption over time. Example causes include global variables, event listeners not being removed, and circular references.

### **Q4: How can you avoid memory leaks in JavaScript?**
**A:**
- Use `let` and `const` instead of `var` to limit scope.
- Remove event listeners when they are no longer needed.
- Nullify object references when they are not required.
- Avoid unnecessary global variables.

