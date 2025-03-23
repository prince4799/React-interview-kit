[Go back](../Index.md)

### **Types of Iterations & Loops in JavaScript**  

JavaScript provides several ways to iterate over data structures like arrays, objects, and other iterables. Here, we’ll cover different types of loops and their behavior.

---

## **1. Traditional Loops**
### **1.1 for Loop**
```js
for (let i = 0; i < 5; i++) {
    console.log(i);
}
```
- Used for iterating over a block of code with a defined number of iterations.
- Suitable for iterating over **arrays** when you need **index control**.

### **1.2 while Loop**
```js
let i = 0;
while (i < 5) {
    console.log(i);
    i++;
}
```
- Runs a block of code **while** the condition is true.
- Useful when the **number of iterations is unknown** in advance.

### **1.3 do...while Loop**
```js
let i = 0;
do {
    console.log(i);
    i++;
} while (i < 5);
```
- Executes **at least once**, then checks the condition.

---

## **Array Iteration Methods & Their Behavior**

| **Method**       | **Returns New Array?** | **Mutates Original Array?** | **Use Case** |
|-----------------|-----------------|----------------|-----------|
| `forEach()`    | ❌ No | ❌ No | Iterating over an array without modifying it |
| `map()`        | ✅ Yes | ❌ No | Creating a new transformed array |
| `filter()`     | ✅ Yes | ❌ No | Creating a filtered array based on conditions |
| `reduce()`     | ⚠️ Depends* | ❌ No | Aggregating array values into a single output (number, object, or array) |
| `some()` / `every()` | ❌ No | ❌ No | Checking conditions on array elements |
| `find()`       | ❌ No | ❌ No | Finding the first matching element |
| `findIndex()`  | ❌ No | ❌ No | Finding the index of the first matching element |
| `sort()`       | ❌ No | ✅ Yes | Sorting an array **(mutates original)** |
| `reverse()`    | ❌ No | ✅ Yes | Reversing an array **(mutates original)** |
| `splice()`     | ✅ Yes (returns removed elements) | ✅ Yes | Adding/removing elements **(mutates original)** |
| `slice()`      | ✅ Yes | ❌ No | Extracting part of an array as a new array |

> ⚠️ **Note:** `reduce()` **does not always return an array**. If you return an array inside the reducer function, then it does, but typically it returns a single value (number, object, or string).

---

## **3. forEach()**
- Iterates over elements but **does not return** a new array.
- Used for side effects like modifying external variables.

```js
const arr = [1, 2, 3];
arr.forEach(num => console.log(num * 2)); 
// Output: 2, 4, 6
```

---

## **4. map()**
- Returns a **new array** with transformed elements.

```js
const arr = [1, 2, 3];
const doubled = arr.map(num => num * 2);
console.log(doubled); // [2, 4, 6]
```

---

## **5. filter()**
- Returns a **new array** containing elements that satisfy a condition.

```js
const arr = [1, 2, 3, 4, 5];
const evenNumbers = arr.filter(num => num % 2 === 0);
console.log(evenNumbers); // [2, 4]
```

---

## **6. reduce()**
- Returns a **single value** after processing all elements.

```js
const arr = [1, 2, 3, 4];
const sum = arr.reduce((acc, num) => acc + num, 0);
console.log(sum); // 10
```

---

## **7. find()**
- Returns the **first matching element**.

```js
const arr = [1, 2, 3, 4];
const found = arr.find(num => num > 2);
console.log(found); // 3
```

---

## **8. sort()**
- **Mutates the original array**.

```js
const arr = [4, 2, 5, 1];
arr.sort((a, b) => a - b);
console.log(arr); // [1, 2, 4, 5]
```

---

### **Conclusion**
- Use **`map()` and `filter()`** when you need a **new array**.
- Use **`forEach()`** for side effects (like logging).
- Use **`reduce()`** when you need to **aggregate values**.
- Be careful with **`sort()` and `splice()`**, as they modify the original array.