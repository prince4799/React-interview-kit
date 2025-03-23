[Go back](../Index.md)

# Promises in JavaScript

## What is a Promise?
A **Promise** in JavaScript is an object representing the eventual completion or failure of an asynchronous operation. It allows handling asynchronous operations in a more readable and manageable way compared to callbacks.

## Promise States
A Promise can be in one of the following states:

| State      | Description |
|------------|------------------------------------------------|
| Pending    | Initial state, neither fulfilled nor rejected. |
| Fulfilled  | The operation was completed successfully. |
| Rejected   | The operation failed. |

## Basic Syntax
```javascript
const myPromise = new Promise((resolve, reject) => {
    let success = true;
    if (success) {
        resolve("Operation successful!");
    } else {
        reject("Operation failed!");
    }
});

myPromise
    .then(result => console.log(result))
    .catch(error => console.log(error));
```

## Promise Chaining
Promise chaining allows multiple asynchronous operations to be executed sequentially.

### Example:
```javascript
function asyncTask1() {
    return new Promise(resolve => {
        setTimeout(() => resolve("Task 1 complete"), 1000);
    });
}

function asyncTask2(previousResult) {
    return new Promise(resolve => {
        setTimeout(() => resolve(previousResult + " -> Task 2 complete"), 1000);
    });
}

asyncTask1()
    .then(result => asyncTask2(result))
    .then(finalResult => console.log(finalResult))
    .catch(error => console.error(error));
```

## Promise Functions
JavaScript provides built-in Promise methods for handling multiple promises:

| Function | Description |
|------------|------------------------------------------------|
| `Promise.all()` | Waits for all promises to resolve, then returns an array of results. If any promise rejects, it immediately rejects. |
| `Promise.race()` | Returns the result of the first resolved or rejected promise. |
| `Promise.allSettled()` | Waits for all promises to settle (resolve or reject) and returns an array with their status. |
| `Promise.any()` | Returns the first resolved promise. If all promises reject, it returns an `AggregateError`. |

### Examples:
```javascript
Promise.all([promise1, promise2, promise3])
    .then(results => console.log(results))
    .catch(error => console.error(error));
```

```javascript
Promise.race([promise1, promise2])
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

```javascript
Promise.allSettled([promise1, promise2, promise3])
    .then(results => console.log(results));
```

```javascript
Promise.any([promise1, promise2, promise3])
    .then(result => console.log(result))
    .catch(error => console.error(error));
```

## Interview Questions on Promises

| Level | Question | Answer |
|------------|------------------------------------------------|------------------------------------------------|
| **Basic** | What is a Promise in JavaScript? | A Promise is an object that represents the eventual completion (or failure) of an asynchronous operation. |
| **Basic** | Explain the different states of a Promise. | Pending: Initial state. Fulfilled: Operation was successful. Rejected: Operation failed. |
| **Basic** | How does the `.then()` and `.catch()` method work in Promises? | `.then()` is used for handling resolved values. `.catch()` is used for handling rejected values. |
| **Basic** | What is the difference between synchronous and asynchronous programming? | Synchronous programming executes tasks sequentially. Asynchronous programming allows tasks to execute independently without blocking execution. |
| **Intermediate** | What are the advantages of using Promises over callbacks? | Avoids callback hell, provides better error handling, and makes code more readable. |
| **Intermediate** | How does Promise chaining work? | Each `.then()` returns a Promise that can be chained with another `.then()`. |
| **Intermediate** | What is the difference between `Promise.all()` and `Promise.race()`? | `Promise.all()` waits for all Promises to resolve or one to reject. `Promise.race()` resolves or rejects as soon as the first Promise settles. |
| **Intermediate** | Explain the differences between `Promise.allSettled()` and `Promise.any()`. | `Promise.allSettled()` returns the status of all promises. `Promise.any()` returns the first resolved promise. |
| **Advanced** | How do you handle errors in a Promise chain? | By using `.catch()` at the end of the chain. |
| **Advanced** | How would you convert a callback-based function into a Promise-based one? | By wrapping the function inside a `new Promise()` and resolving/rejecting based on the callback results. |
| **Advanced** | What is the difference between `async/await` and Promises? | `async/await` is syntactic sugar over Promises, making asynchronous code look synchronous. |
| **Advanced** | Can you cancel a Promise once it starts executing? | No, JavaScript Promises cannot be canceled natively, but you can use workarounds like abort controllers. |

