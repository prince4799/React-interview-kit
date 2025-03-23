[Go back](../Index.md)

# Arrays & Types of Operations

## Introduction to Arrays
An **array** in JavaScript is a special variable that can hold multiple values at once. Arrays are zero-indexed and allow various operations for adding, removing, and manipulating elements.

### Creating Arrays
```javascript
let arr1 = [1, 2, 3, 4, 5]; // Array with numbers
let arr2 = ['apple', 'banana', 'cherry']; // Array with strings
let arr3 = new Array(5); // Creates an empty array with length 5
```

---

## Types of Operations

### 1. Adding Elements
- **push()** – Adds elements to the end
- **unshift()** – Adds elements to the beginning

```javascript
let fruits = ['apple', 'banana'];
fruits.push('cherry'); // ['apple', 'banana', 'cherry']
fruits.unshift('mango'); // ['mango', 'apple', 'banana', 'cherry']
```

### 2. Removing Elements
- **pop()** – Removes the last element
- **shift()** – Removes the first element

```javascript
let numbers = [10, 20, 30, 40];
numbers.pop(); // [10, 20, 30]
numbers.shift(); // [20, 30]
```

### 3. Iterating Over Arrays
- **forEach()** – Loops through each element
- **map()** – Returns a new array with modified elements

```javascript
let nums = [1, 2, 3, 4];
nums.forEach(num => console.log(num * 2)); // 2, 4, 6, 8
let squared = nums.map(num => num * num); // [1, 4, 9, 16]
```

### 4. Searching in Arrays
- **indexOf()** – Returns the index of the first occurrence
- **includes()** – Checks if an element exists

```javascript
let arr = [5, 10, 15, 20];
console.log(arr.indexOf(10)); // 1
console.log(arr.includes(15)); // true
```

### 5. Filtering and Transforming
- **filter()** – Returns a new array with elements that match a condition
- **reduce()** – Accumulates values into a single result

```javascript
let numbersArray = [10, 15, 20, 25, 30];
let filtered = numbersArray.filter(num => num > 20); // [25, 30]
let sum = numbersArray.reduce((acc, num) => acc + num, 0); // 100
```

### 6. Sorting and Reversing
- **sort()** – Sorts elements alphabetically by default
- **reverse()** – Reverses the order

```javascript
let names = ['Zara', 'Alice', 'Mike'];
names.sort(); // ['Alice', 'Mike', 'Zara']
names.reverse(); // ['Zara', 'Mike', 'Alice']
```

---

## Most Asked Interview Questions

1. **How do you remove duplicates from an array?**
```javascript
let array = [1, 2, 2, 3, 4, 4, 5];
let uniqueArray = [...new Set(array)]; // [1, 2, 3, 4, 5]
```

2. **What is the difference between map() and forEach()?**
   - `map()` returns a new array.
   - `forEach()` does not return a new array, only iterates.

3. **How do you flatten a nested array?**
```javascript
let nested = [1, [2, [3, 4]], 5];
console.log(nested.flat(2)); // [1, 2, 3, 4, 5]
```

4. **How to find the largest number in an array?**
```javascript
let numbers = [10, 25, 5, 40];
console.log(Math.max(...numbers)); // 40
```

5. **How to shuffle elements randomly?**
```javascript
let array = [1, 2, 3, 4, 5];
array.sort(() => Math.random() - 0.5);
```

6. **How do you merge two arrays without duplicates?**
```javascript
let arr1 = [1, 2, 3];
let arr2 = [3, 4, 5];
let merged = [...new Set([...arr1, ...arr2])]; // [1, 2, 3, 4, 5]
```



