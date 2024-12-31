### Setting up Package Json File with Webpack

```js
{
  "name": "redux-starter",
  "version": "1.0.0",
  "description": "Redux Starter Project",
  "main": "index.js",
  "scripts": {
    "start": "webpack serve --config ./webpack.config.js"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^5.89.0",
    "webpack-cli": "^4.10.0",
    "webpack-dev-server": "^4.15.1"
  }
}

```

### Scripts

```js
"scripts": {
  "start": "webpack serve --config ./webpack.config.js"
}
```

### Purpose of `scripts` in `package.json`

The `scripts` section in the `package.json` file allows developers to define custom commands that can be executed using `npm run <script-name>`. These scripts simplify repetitive or complex tasks such as building, testing, or running a development server.

For instance, the provided `start` script in your example is defined as:


### What This Script Does

1.  **Runs Webpack Dev Server**:

    -   The script invokes the `webpack-dev-server`, which is a powerful tool for local development. It serves your application, watches for file changes, and refreshes the browser automatically.
2.  **Specifies Configuration**:

    -   The `--config ./webpack.config.js` flag tells Webpack to use the `webpack.config.js` file located in the project root. This file defines Webpack's behavior, such as entry points, output directory, loaders, and plugins.
3.  **Development Workflow**:

    -   When a developer runs `npm start`, Webpack compiles the code and starts a local server (default port 3000). This server provides live reload or hot module replacement (HMR) for an enhanced development experience.


### Web Pack Dev Dependencies

**Purpose**:

-   **`devDependencies`**: Contains packages required only during development (not needed in production).
-   The key dependencies for using Webpack are listed here:
    -   **`webpack`**: The core Webpack library. Used for bundling JavaScript, CSS, and other assets.
    -   **`webpack-cli`**: Provides a command-line interface for Webpack, allowing you to run Webpack commands.
    -   **`webpack-dev-server`**: A development server for Webpack. Enables features like live reloading and hot module replacement (HMR).