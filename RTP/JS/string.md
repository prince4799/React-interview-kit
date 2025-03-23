[Go back](../Index.md)

# **Strings & Types of Operations in JavaScript**

## **1. Introduction to Strings**
In JavaScript, a string is a sequence of characters enclosed in quotes:
```js
let str1 = "Hello";  // Double quotes
let str2 = 'World';  // Single quotes
let str3 = `Hello, ${str2}!`; // Template literals
```

## **2. String Properties & Methods**
Strings are immutable, meaning operations on strings return a new string instead of modifying the original.

### **2.1 String Properties**
| Property | Description |
|----------|-------------|
| `length` | Returns the length of the string |

Example:
```js
let text = "JavaScript";
console.log(text.length); // 10
```

### **2.2 String Methods**
| Method | Returns New String? | Description |
|--------|----------------|-------------|
| `charAt(index)` | ❌ No | Returns the character at the given index |
| `charCodeAt(index)` | ❌ No | Returns the Unicode of the character at index |
| `toUpperCase()` | ✅ Yes | Converts the string to uppercase |
| `toLowerCase()` | ✅ Yes | Converts the string to lowercase |
| `trim()` | ✅ Yes | Removes whitespace from both ends of the string |
| `trimStart()` / `trimEnd()` | ✅ Yes | Removes whitespace from the start or end |
| `concat(str)` | ✅ Yes | Joins two or more strings |
| `split(delimiter)` | ✅ Yes (Array) | Splits the string into an array |
| `substring(start, end)` | ✅ Yes | Extracts part of a string (excluding `end` index) |
| `slice(start, end)` | ✅ Yes | Extracts part of a string (supports negative indexes) |
| `replace(old, new)` | ✅ Yes | Replaces the first occurrence of `old` with `new` |
| `replaceAll(old, new)` | ✅ Yes | Replaces all occurrences of `old` with `new` |
| `includes(substr)` | ❌ No (Boolean) | Checks if the string contains `substr` |
| `indexOf(substr)` | ❌ No (Number) | Returns the first index of `substr`, or `-1` if not found |
| `lastIndexOf(substr)` | ❌ No (Number) | Returns the last index of `substr`, or `-1` if not found |
| `startsWith(substr)` | ❌ No (Boolean) | Checks if the string starts with `substr` |
| `endsWith(substr)` | ❌ No (Boolean) | Checks if the string ends with `substr` |
| `repeat(n)` | ✅ Yes | Repeats the string `n` times |

Example Usage:
```js
let text = "  JavaScript  ";
console.log(text.trim()); // "JavaScript"
console.log(text.toUpperCase()); // "  JAVASCRIPT  "
console.log(text.includes("Script")); // true
console.log(text.split(" ")); // ["", "", "JavaScript", "", ""]
```

## **3. String Template Literals**
Template literals use backticks (`) and allow embedding expressions:
```js
let name = "Alice";
let greeting = `Hello, ${name}!`;
console.log(greeting); // "Hello, Alice!"
```

### **Multi-line Strings with Template Literals**
```js
let multiLine = `This is line 1
This is line 2`;
console.log(multiLine);
```

## **4. String Escape Characters**
| Escape Sequence | Description |
|----------------|-------------|
| `\'` | Single quote |
| `\"` | Double quote |
| `\\` | Backslash |
| `\n` | New line |
| `\t` | Tab |
| `\r` | Carriage return |

Example:
```js
console.log("Hello\nWorld"); // New line
console.log("I\'m learning JavaScript!"); // I'm learning JavaScript!
```

## **5. Comparing Strings**
JavaScript compares strings using lexicographic order:
```js
console.log("apple" > "banana"); // false (compares character codes)
console.log("10" > "2"); // false (strings are compared lexicographically)
```

Use `.localeCompare()` for locale-aware comparison:
```js
console.log("a".localeCompare("b")); // -1 (a < b)
console.log("b".localeCompare("a")); // 1 (b > a)
```

