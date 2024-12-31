# Compose and Pipe From Lodash

### Notes on Solving Function Composition Structure with Lodash Library

In functional programming, we use **function composition** to combine multiple functions. However, as the number of functions increases, the composition can become difficult to read due to nested function calls. To solve this, we can use libraries like **Lodash** to simplify function composition.

* * * * *

### 1\. **Problem with Nested Function Calls**

-   As functions are composed together, the expression may become hard to read, especially with multiple nested functions.

```js
let message = generateMessage(convertToUpper(trimUsername(username)));
```

-   This structure can get complex as more functions are added.

### 2\. **Using Lodash to Solve the Structure Issue**

-   **Lodash** is a popular library for working with arrays and objects and provides several utility functions for functional programming.
-   Lodash's `compose` function helps by composing multiple functions in reverse order to improve readability.

### 3\. **Installing Lodash**

-   To use Lodash, first install the library via terminal:

`npm install lodash`

### 4\. **Importing Lodash Functions**

-   At the top of your file, import the necessary Lodash functions:


`import { compose } from 'lodash/fp'; // Importing the compose function`

### 5\. **Using `compose` to Simplify Function Composition**

-   With `compose`, we can combine functions in a cleaner way:
    -   **`compose`** takes functions as arguments and executes them in reverse order, from right to left.



```js
const composedFunction = compose(generateMessage, convertToUpper, trimUsername);
```

-   Here's how the composition works:

    1.  `trimUsername` is applied first.
    2.  The output of `trimUsername` is passed to `convertToUpper`.
    3.  The output of `convertToUpper` is passed to `generateMessage`.
-   Now, instead of manually chaining function calls, we can call `composedFunction` with the username:



```js
let result = composedFunction(username);
console.log(result); // Output: "HELLO HARLEY GOOD MORNING"
```



### 6\. **Improving Readability with `pipe`**

-   In some cases, you may want to read the expression from left to right (as it naturally flows). Lodash provides the **`pipe`** function for this purpose.
-   **`pipe`** allows functions to be composed in their **original order** (left to right).

```js
import { pipe } from 'lodash/fp'; // Importing pipe from Lodash

const pipedFunction = pipe(trimUsername, convertToUpper, generateMessage);
```



-   Now, the expression flows logically from left to right:

    1.  First, `trimUsername` is applied.
    2.  Then, `convertToUpper` is applied.
    3.  Finally, `generateMessage` is applied.
-   Call the `pipedFunction` with the username:

```js
let result = pipedFunction(username);
console.log(result); // Output: "HELLO HARLEY GOOD MORNING"

```

### 7\. **Benefits of Using Lodash Functions**

-   **Improved readability**: By using `compose` or `pipe`, the code becomes much more readable, reducing the complexity of nested function calls.
-   **Modularity**: Functions remain modular and reusable. You can easily add, remove, or reorder functions without affecting the rest of the code.
-   **Cleaner structure**: Using Lodash's `pipe` and `compose` allows you to maintain a clear and simple structure in your code.

* * * * *

By leveraging Lodash's `compose` and `pipe`, we can improve the clarity of function compositions, making code easier to read and maintain, while preserving the power of functional programming.