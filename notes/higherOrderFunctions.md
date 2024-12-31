# Higher Order Functions in JavaScript

### 1\. **What is a Higher-Order Function?**

-   A **higher-order function** is a function that:

    -   Takes one or more functions as arguments **or**
    -   Returns a function (or both).
-   In simple terms, higher-order functions either accept functions as input or produce functions as output, or both.

### 2\. **Examples of Higher-Order Functions**

**a. `setTimeout` Function**

-   The `setTimeout` function is a built-in JavaScript function that accepts a function as a parameter.
-   It schedules the execution of the function after a specified delay.

Example:

```js 
setTimeout(function() {
  console.log("This message will be shown after 2 seconds");
}, 2000);
```

-   In this case, the function passed to `setTimeout` is executed after the specified time interval (2000 milliseconds). Since `setTimeout` takes a function as an argument, it is considered a higher-order function.

**b. `map` Function (Array Method)**

-   The `map()` method on arrays is another example of a higher-order function.
-   The `map()` function takes a function as a parameter and applies that function to each item in the array, returning a new array.

Example:

```js
let numbers = [1, 2, 3, 4];
let result = numbers.map(function(num) {
  return num * 10;
});

console.log(result); // Output: [10, 20, 30, 40]
```

-   In this example, the `map()` function takes a function (which multiplies each item by 10) as its argument and applies it to every element in the `numbers` array.

### 3\. **Summary**

-   A **higher-order function** is a function that either:
    -   Takes a function as a parameter.
    -   Returns a function.
-   Examples of higher-order functions in JavaScript include `setTimeout` (which takes a function as an argument) and array methods like `map` (which also takes a function as an argument).

* * * * *

By understanding higher-order functions, you'll be able to write more flexible and reusable code, leveraging JavaScript's functional programming capabilities.