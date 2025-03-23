[Go back](../Index.md)

# Closure

A **closure** is a function that remembers the variables from its **lexical scope** even after the outer function has finished execution.

## Example
```js
function outerFunction() {
  let count = 0;

  return function innerFunction() {
    count++;
    console.log(count);
  };
}

const counter = outerFunction();
counter(); // 1
counter(); // 2
```

### Why Does it Work?
The `innerFunction()` still has access to `count`, even though `outerFunction()` has already executed. This is because of closures.


