[Go back](../Index.md)

# Async-Await in JavaScript

## **1. Introduction to Async-Await**

`async` and `await` are modern JavaScript features introduced in ES2017 (ES8) that simplify handling asynchronous code. They make working with promises easier and more readable by allowing us to write asynchronous code that looks synchronous.

## **2. How Async-Await Works?**
- `async` is used before a function to make it return a promise.
- `await` is used inside an `async` function to pause execution until a promise resolves.

### **Example: Using Async-Await**
```javascript
function fetchData() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve("Data received");
        }, 2000);
    });
}

async function getData() {
    console.log("Fetching data...");
    const result = await fetchData();
    console.log(result); // Output: Data received
}

getData();
```

## **3. Comparison: Async-Await vs Promises vs Callbacks**

| Feature | Async-Await | Promises | Callbacks |
|---------|------------|----------|-----------|
| Readability | High (looks like synchronous code) | Moderate | Low (Callback Hell) |
| Error Handling | Uses `try...catch` | `.catch()` method | Nested error handling |
| Chaining | Simple with `await` | Uses `.then()` chaining | Complex nesting |
| Debugging | Easier | Harder | Very difficult |

## **4. Handling Errors in Async-Await**

```javascript
async function fetchDataWithError() {
    try {
        let response = await fetch("https://invalid-url.com");
        let data = await response.json();
        console.log(data);
    } catch (error) {
        console.error("Error fetching data:", error);
    }
}

fetchDataWithError();
```

## **5. Most Asked Interview Questions on Async-Await**

### **Q1: What is Async-Await in JavaScript?**
**Answer:**
Async-Await is a feature in JavaScript introduced in ES8 that allows asynchronous code to be written in a synchronous-like manner. `async` makes a function return a promise, and `await` pauses execution until the promise is resolved.

---

### **Q2: How does Async-Await work internally?**
**Answer:**
- When an `async` function is called, it returns a Promise.
- The function execution is paused at each `await` keyword until the awaited Promise is resolved.
- The rest of the function executes once the Promise is resolved.
- Errors can be caught using `try...catch`.

---

### **Q3: What are the advantages of using Async-Await?**
**Answer:**
1. **Improved Readability** – Code appears synchronous and is easier to follow.
2. **Better Error Handling** – Uses `try...catch` instead of `.catch()`.
3. **Avoids Callback Hell** – Reduces deeply nested callback structures.
4. **Easy Debugging** – Debuggers handle async functions better.

---

### **Q4: Can we use Async-Await without Promises?**
**Answer:**
No, `async` functions always return a promise. `await` works only with promises, meaning it cannot be used with standard callback functions or synchronous functions.

---

### **Q5: What happens if an Async function does not return a promise?**
**Answer:**
If an `async` function does not explicitly return a promise, JavaScript automatically wraps the returned value in a promise.

Example:
```javascript
async function example() {
    return "Hello"; // JavaScript wraps it in a Promise
}

example().then(console.log); // Output: Hello
```

---

### **Q6: How to handle multiple async operations sequentially?**
**Answer:**
Use `await` sequentially within an `async` function.
```javascript
async function fetchData() {
    let user = await getUser();
    let orders = await getOrders(user.id);
    let details = await getOrderDetails(orders[0].id);
    console.log(details);
}
```

---

### **Q7: How to handle multiple async operations in parallel?**
**Answer:**
Use `Promise.all()` to run promises concurrently.
```javascript
async function fetchParallel() {
    let [user, orders] = await Promise.all([getUser(), getOrders()]);
    console.log(user, orders);
}
```

---

### **Q8: How does Error Propagation work in Async-Await?**
**Answer:**
Errors inside an `async` function reject the returned promise. They can be caught using `try...catch` or a `.catch()` method.
```javascript
async function errorExample() {
    throw new Error("Something went wrong");
}

errorExample().catch(console.error);
```

---

## **6. Conclusion**
Async-Await simplifies working with asynchronous code, improving readability, error handling, and debugging. It is widely used in modern JavaScript applications, especially in handling API requests and async operations.

