[Go back](../Index.md)

# Promises vs Callbacks vs Async-Await

## 1. Introduction
Handling asynchronous operations in JavaScript can be done using **callbacks, promises, and async-await**. Each approach has its advantages and disadvantages, making it important to understand when to use which.

## 2. Explanation
### **Callbacks**
A callback function is a function passed as an argument to another function, allowing asynchronous execution.

#### Example:
```js
function fetchData(callback) {
    setTimeout(() => {
        callback("Data fetched");
    }, 1000);
}

fetchData((message) => {
    console.log(message);
});
```
#### Drawbacks:
- Leads to **callback hell** (nested callbacks making code unreadable)
- Difficult to handle errors
- Hard to manage multiple async operations

---
### **Promises**
Promises solve callback hell by providing a more structured way to handle asynchronous operations.

#### Example:
```js
function fetchData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data fetched");
        }, 1000);
    });
}

fetchData().then((message) => console.log(message)).catch((error) => console.error(error));
```
#### Benefits:
- Avoids callback hell with `.then()` chaining
- Provides built-in error handling with `.catch()`
- Can run multiple async tasks in parallel using `Promise.all()`

---
### **Async-Await**
Async-Await is a syntactic sugar over promises, making asynchronous code look synchronous.

#### Example:
```js
async function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data fetched");
        }, 1000);
    });
}

async function getData() {
    const message = await fetchData();
    console.log(message);
}

getData();
```
#### Benefits:
- **Easier to read and write**
- **Better error handling** using `try-catch`
- **More maintainable** than Promises or Callbacks

## 3. Comparison Table
| Feature         | Callbacks | Promises | Async-Await |
|----------------|----------|----------|-------------|
| Readability    | ❌ Hard to read (Callback Hell) | ✅ Better than Callbacks | ✅ Best readability |
| Error Handling | ❌ Error-prone | ✅ `.catch()` | ✅ `try-catch` |
| Chaining       | ❌ Nested callbacks | ✅ `.then()` chaining | ✅ Uses `await` |
| Debugging      | ❌ Hard to debug | ✅ Easier than callbacks | ✅ Best for debugging |
| Parallel Execution | ❌ Difficult | ✅ `Promise.all()` | ✅ `await Promise.all()` |

## 4. Most Asked Interview Questions
### **Q1: What is the difference between Callbacks, Promises, and Async-Await?**
#### **Answer:**
- Callbacks are functions passed as arguments to handle async operations but can lead to callback hell.
- Promises are objects that represent a future value with `.then()`, `.catch()`, and `.finally()`.
- Async-Await is a modern syntax for handling promises in a more readable way.

---
### **Q2: Why is Async-Await preferred over Promises?**
#### **Answer:**
- Async-Await makes code more readable and maintainable.
- It provides better error handling using `try-catch`.
- It avoids `.then()` chaining and makes the code look synchronous.

---
### **Q3: Can you use Async-Await with Promises?**
#### **Answer:**
Yes! Async-Await is built on top of Promises.
Example:
```js
async function fetchData() {
    return await new Promise((resolve) => setTimeout(() => resolve("Data fetched"), 1000));
}
fetchData().then(console.log);
```

---
### **Q4: Does Async-Await block the event loop?**
#### **Answer:**
No, Async-Await does not block the event loop. It still allows other operations to continue while waiting for the async task to complete.

---
### **Q5: How do you handle errors in Async-Await?**
#### **Answer:**
Use `try-catch` block:
```js
async function fetchData() {
    try {
        let response = await fetch('https://api.example.com/data');
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error fetching data", error);
    }
}
fetchData();
```

## 5. Conclusion
- Use **Callbacks** only for simple async operations.
- Use **Promises** for better async handling and parallel execution.
- Use **Async-Await** for best readability and maintainability.

