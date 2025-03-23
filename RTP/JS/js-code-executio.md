#### [Go back](../Index.md)

# JavaScript Code Execution

## Q1: How does JavaScript execute code?
**Answer:**  
JavaScript is a **single-threaded** language that executes code in a synchronous manner using the **Execution Context** and **Call Stack**. However, it can handle asynchronous operations using the **Event Loop**, which interacts with the **Call Stack**, **Web APIs**, and **Task Queues** to process asynchronous code.

---

## Q2: What is the Call Stack, and how does it work?
**Answer:**  
The **Call Stack** is a **LIFO (Last In, First Out)** data structure that keeps track of function calls. When a function is invoked, it is **pushed** onto the stack, and when it completes execution, it is **popped** off the stack. If the stack overflows (due to excessive recursion or infinite loops), a **stack overflow error** occurs.

---

## Q3: What is the Event Loop in JavaScript?
**Answer:**  
The **Event Loop** is a mechanism that allows JavaScript to handle asynchronous tasks efficiently. It continuously checks the **Call Stack**, and if it is empty, it moves pending tasks from the **Callback Queue** or **Micro-task Queue** to the Call Stack for execution.

---

## Q4: What are Task Queues in JavaScript?
**Answer:**  
JavaScript has two main task queues:
1. **Micro-task Queue (Priority Queue):** Handles promises (`.then()`, `catch`, `finally`), `MutationObserver`, and `queueMicrotask()`.
2. **Macro-task Queue (Callback Queue):** Handles `setTimeout`, `setInterval`, `setImmediate`, `I/O operations`, and `DOM events`.

---

## Q5: What is the difference between the Micro-task Queue and Macro-task Queue?
**Answer:**  
- The **Micro-task Queue** has higher priority and executes immediately after the current function execution completes, before checking the Call Stack again.
- The **Macro-task Queue** (callback queue) runs after all micro-tasks are completed.

---

## Q6: Can you explain how JavaScript executes asynchronous code with an example?
**Answer:**  
```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout Callback");
}, 0);

Promise.resolve().then(() => console.log("Promise resolved"));

console.log("End");
```

**Output:**  
```
Start  
End  
Promise resolved  
Timeout Callback  
```

**Explanation:**  
1. `"Start"` is logged immediately.
2. `setTimeout()` is placed in the **Macro-task Queue**.
3. `Promise.resolve()` is placed in the **Micro-task Queue**.
4. `"End"` is logged immediately.
5. Micro-tasks (`Promise resolved`) execute before Macro-tasks (`Timeout Callback`).

---

Would you like to add more questions on this topic or move to the next one? 🚀

