# Functions in JavaScript

We will explore the basic concepts of functions in JavaScript, emphasizing that functions are treated as first-class citizens. This means that functions can be handled just like any other variable in JavaScript.


### 1\. **Functions as First-Class Citizens**

-   In JavaScript, **functions are first-class objects**. This means they can:
    -   Be assigned to variables
    -   Be passed as arguments to other functions
    -   Be returned from other functions

### 2\. **Assigning Functions to Variables**

-   Functions can be assigned to variables without invoking them. When assigned, the function reference is stored in the variable.


```js
function greeting() {
  return "Good morning";
}

// Assign the function to a variable
let message = greeting;
console.log(message()); // Output: Good morning

```

- Notice that we didn’t call the greeting() function directly. Instead, we assigned its reference to the variable message, which when called gives the same result.


### 3\. **Passing Functions as Arguments**

- JavaScript functions can be passed as arguments to other functions

```js
function printMessage(func) {
  console.log(func());
}

// Passing greeting function as argument
printMessage(greeting); // Output: Good morning

```
- Here, greeting is passed as an argument to printMessage, which invokes the function inside printMessage.


### 4\. **Returning Functions from Other Functions**

- Functions can also return other functions, which is a key concept in functional programming.

```js
function createGreeting() {
  return function() {
    return "Good morning";
  };
}

let newGreeting = createGreeting();
console.log(newGreeting()); // Output: Good morning

```

- In this case, the createGreeting() function returns an anonymous function that contains the message. When newGreeting() is called, it outputs the message.

### 5\. **Why Return Functions?**

-   Returning functions is a powerful technique in **functional programming**. It allows for:
    -   **Closure**: Functions returned from other functions can maintain access to variables defined in the outer function's scope.
    -   **Customization**: Functions can generate new behavior dynamically.

### 6\. **Summary**

-   Functions in JavaScript are treated like variables, and can be assigned, passed as arguments, and returned.
-   This flexibility opens up many programming techniques, especially in **functional programming**, where higher-order functions (functions that take other functions as arguments or return them) are commonly used.

