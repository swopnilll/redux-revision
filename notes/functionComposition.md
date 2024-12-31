# Function Composition in Javascript

### Notes on Function Composition and Building Complex Functions

In functional programming, we break down tasks into smaller, reusable functions and **compose** them to solve more complex problems. This approach is known as **function composition**. Here's an explanation of the concepts:

* * * * *

### 1\. **Problem Breakdown with Functions**

-   We can take a task and split it into smaller tasks, where each task is handled by a dedicated function. These small functions can then be **composed** to build more complex functionality.

Example:

-   Suppose we have a task where we need to:
    1.  Remove unwanted spaces from a username.
    2.  Generate a greeting message with the username.

### 2\. **Traditional Approach (Step-by-Step)**

-   We could manually perform each operation:
    -   First, **trim** the username by removing spaces from the beginning and end.
    -   Then, create a greeting message by adding "Hello" at the beginning and "Good morning" at the end.

Example (Traditional Way):

```js
let username = "  Harley  ";
let trimmedUsername = username.trim(); // Trimming spaces
let message = "Hello " + trimmedUsername + " Good morning";
console.log(message); // Output: "Hello Harley Good morning"

```

### 3\. **Functional Programming Approach**

-   Instead of doing everything in a single block of code, we break the tasks into **smaller functions**:
    -   One function for **trimming** the username.
    -   Another function for **generating** the greeting message.

Example (Functional Approach):

```js
// Function to trim the username
function trimUsername(name) {
  return name.trim();
}

// Function to generate the greeting message
function generateMessage(name) {
  return `Hello ${name} Good morning`;
}

// Using function composition
let username = "  Harley  ";
let trimmedUsername = trimUsername(username);
let message = generateMessage(trimmedUsername);
console.log(message); // Output: "Hello Harley Good morning"

```

-   This approach allows us to focus on small, specific tasks. Each function has a clear responsibility, making the code more modular and easier to maintain.

### 4\. **Composing Functions**

-   **Function composition** refers to combining multiple small functions to form a more complex function or behavior.
-   We can **chain** functions together, where the output of one function becomes the input for the next function.

Example:

-   We can create additional functions to handle other tasks, like converting the username to **uppercase**.

```js
// Function to convert name to uppercase
function convertToUpper(name) {
  return name.toUpperCase();
}

let result = convertToUpper(trimmedUsername);
let message = generateMessage(result);
console.log(message); // Output: "Hello HARLEY Good morning"

```

### 5\. **Challenges in Function Composition**

-   **Right to Left Execution**: When composing multiple functions, the order of execution is important. For example, in the case of converting the name to uppercase before generating the message, we have to read the expression from right to left.

Example:

```js
`let message = generateMessage(convertToUpper(trimUsername(username)));`
```

-   As more functions are added, the expression can become harder to read and manage, especially with many nested function calls.

-   This complexity can lead to difficulty in maintaining code when there are many functions involved.