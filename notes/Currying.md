# Currying 

In Compose and Pipe section we had: 

```js
const trimUsername = (name) => name.trim();
const convertToUpper = (name) => name.toUpperCase();
const generateMessage = (name) => `Hello, ${name}. Good morning!`;

const pipedFunction = pipe(trimUsername, convertToUpper, generateMessage);

console.log(pipedFunction("   Harley   ")); // Output: "Hello, HARLEY. Good morning!"
```

- what if: 

```js
const generateMessage = (name, value) => `Hello, ${name}. Good morning! ${value}`;

const pipedFunction = pipe(trimUsername, convertToUpper, generateMessage);

console.log(pipedFunction("   Harley   ")); // Output: "Hello, HARLEY. Good morning!"
```

In the case where the `generateMessage` function requires two arguments (i.e., `name` and `value`), you can't directly use `pipe` because it expects each function in the pipeline to have a **single** input. Since `generateMessage` requires two arguments, the `pipe` function would not be able to handle it directly.

However, you can solve this by **partially applying** the function, which means you can create a new function that automatically fills in the second argument (`value`) while leaving the first argument (`name`) to be passed through the pipeline.

Here's how you can do it:

### 1\. **Create a partially applied version of `generateMessage`**

You can use a **curried function** to handle the two arguments. This will allow you to pass the second argument (`value`) after all the other functions in the pipeline are applied.

For example:

```js
const trimUsername = (name) => name.trim();
const convertToUpper = (name) => name.toUpperCase();
const generateMessage = (value) => (name) => `Hello, ${name}. Good morning! ${value}`;

const pipedFunction = pipe(trimUsername, convertToUpper, generateMessage("Have a nice day"));

console.log(pipedFunction("   Harley   ")); // Output: "Hello, HARLEY. Good morning! Have a nice day"
```

### Explanation:

1.  **`generateMessage`** is modified to be a curried function. It returns a function that takes `name` as an argument, and this allows us to pass the second argument (`value`) first. This is known as partial application.
    -   `generateMessage("Have a nice day")` returns a new function that takes `name` and generates the message with the value `"Have a nice day"`.
2.  **`pipe`** works as before:
    -   The input (`" Harley "`) is first passed to `trimUsername`, which trims the spaces, resulting in `"Harley"`.
    -   Then, `"Harley"` is passed to `convertToUpper`, resulting in `"HARLEY"`.
    -   Finally, `"HARLEY"` is passed to the curried version of `generateMessage`, and it produces the final message `"Hello, HARLEY. Good morning! Have a nice day"`.


**currying** is explained as a popular technique in functional programming, which is used to transform functions that take multiple parameters into a series of functions that each take a single argument.

### Key Concepts:

1.  **Problem Overview:**

    -   The example involves generating a greeting message, but we want to dynamically change the greeting message.
    -   When we attempt to pass a variable (`message`) into a function, the pipeline logic breaks because of how the functions are composed. The `generateMessage` function, which expects two arguments, is instead receiving a string as the first argument and `undefined` as the second.
2.  **Currying:**

    -   **Currying** is the technique of transforming a function that takes multiple arguments into a series of functions that each take a single argument.
    -   In the example, a function that multiplies two numbers is transformed into a curried function, which takes one argument at a time:

       ```js
        const multiply = (a) => (b) => a * b;
        const result = multiply(2)(5); // 10

       ```

      
    -   This technique allows for better flexibility in function composition.
3.  **Applying Currying to the Greeting Message:**

    -   The `generateMessage` function, which originally took two parameters (`message` and `name`), is now transformed into a curried function.
    -   Using **arrow function syntax**, the function is modified to return a new function when the first parameter (`message`) is passed:

    ```js
    const generateMessage = (message) => (name) => `Hello, ${name}. ${message}`;
    ```

       

    -   This way, we can pass the `message` first, and the function will return a new function that takes the `name`.
4.  **Result:**

    -   When the function is called, it behaves as expected, allowing us to pass different messages dynamically:

        ```js
         const result = generateMessage("Good morning")("Harley"); // "Hello, Harley. Good morning"
        ```

### Summary:

-   **Currying** allows us to transform functions with multiple parameters into functions with a single parameter, making them more flexible and easier to compose.
-   This technique is useful when you want to create reusable functions that can be applied in various scenarios with different arguments.