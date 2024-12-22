# 🚀 Initial Setup Checklist for Node Project

This guide provides a structured approach to setting up an Node project with best practices for development. The checklist and steps ensure consistency and maintainability across the project lifecycle.

---

## **Checklist**

- [x] **Git setup**
- [x] **Node version manager setup**
- [x] **Node.js project setup**
- [x] **TypeScript setup**
- [x] **Prettier setup**
- [x] **ESLint setup**
- [x] **Git hooks setup**
- [x] **Application config setup**
- [x] **Express app setup**
- [x] **Logger setup**
- [x] **Error handling setup**
- [x] **Tests setup**

---

## **Step 1: Git Setup**

Version control is essential for collaboration and tracking changes. Follow these steps to set up Git for your project:

### 1. **Create a `.gitignore` file**

- Use a `.gitignore` generator or extension to create a file tailored for Node.js projects.
- Example content for `.gitignore`:
  ```plaintext
  node_modules
  .env
  dist
  .DS_Store
  ```

### 2. **Initialize Git**

Open the terminal in the project directory and run:

```bash
git init
```

### 3. **Add Files to Staging**

Add all project files to the Git staging area:

```bash
git add .
```

### 4. **Commit Files**

Create your first commit with an appropriate message:

```bash
git commit -m "Add .gitignore file"
```

### 5. **Push to a Remote Repository**

If you have a remote Git repository set up (e.g., GitHub, GitLab):

- Add the remote repository:
  ```bash
  git remote add origin <REMOTE_REPOSITORY_URL>
  ```
- Push the code:
  ```bash
  git branch -M main
  git push -u origin main
  ```

---

## **Step 2: Node Version Manager (NVM) Setup**

Node Version Manager (NVM) is a version manager for Node.js that allows you to easily install, switch between, and manage multiple versions of Node.js on your system. This is particularly useful when working on different projects that may require different versions of Node.js.

---

### **Guide to NVM Setup**

Follow these steps to set up NVM and configure it for your project:

#### **1. Install NVM**

- Visit the official NVM GitHub repository: [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)
- Follow the installation instructions for your operating system.

#### **2. Create a `.nvmrc` File**

- In the root of your project directory, create a `.nvmrc` file to specify the Node.js version required for the project.
- Add the latest **LTS** version (e.g., `v22.12.0`) to the file:
  ```bash
  "v22.12.0"
  ```

#### **3. Use the Specified Node.js Version**

- Run the following command to use the Node.js version specified in the `.nvmrc` file:
  ```bash
  nvm use
  ```

#### **4. Install the Specified Version (if not already installed)**

- If the version specified in `.nvmrc` is not installed, install it using:
  ```bash
  nvm install v22.12.0
  ```

#### **5. Confirm the Node.js Version**

- Verify that the correct version is in use:
  ```bash
  node -v
  ```

---

### **Additional Notes**

- **Project Consistency**: Ensure all team members use the same Node.js version by including the `.nvmrc` file in version control.

- **Switching Versions**: If you switch projects frequently, running `nvm use` in the project directory will automatically apply the appropriate version.

- **Global Packages**: Use project-specific dependency management (e.g., `package.json`) instead of relying on globally installed packages.

---

## **Step 3: Node.js Project Setup**

This step involves setting up a basic Node.js project structure, initializing npm, and adding a development script.

### **Steps**

Follow these steps to set up node project:

#### **1. Create Folder and Files**

- Create a folder named `src` in the root directory.
- Inside the `src` folder, create a file named `server.js`.
- Add the following code to `server.js` to test the setup:
  ```javascript
  // src/server.js
  console.log("Node.js server is running!");
  ```

#### **2. Initialize the Node.js Project**

- Navigate to the root directory of your project in the terminal.
- Run the following command to initialize the project and create a `package.json` file:
  ```bash
  npm init -y
  ```

#### **3. Add a Development Script**

- Open the `package.json` file.
- Add the following script under the `scripts` section:
  ```json
  "scripts": {
    "dev": "node src/server.js"
  }
  ```

#### **4. Test the Setup**

- Run the development script to verify everything works:
  ```bash
  npm run dev
  ```
- You should see the following message in the terminal:
  ```
  Node.js server is running!
  ```

By following these steps, you will have a basic Node.js project setup that is ready for further development.

---

## **Step 4: TypeScript Setup**

This step involves setting up TypeScript in your Node.js project and configuring it to compile TypeScript files into JavaScript.

### **Steps**

#### **1. Install TypeScript**

- Install TypeScript as a development dependency:
  ```bash
  npm i -D typescript
  ```

#### **2. Rename JavaScript Files to TypeScript**

- Example- Rename the `server.js` file in the `src` folder to `server.ts`.

#### **3. Initialize TypeScript Configuration**

- Create a `tsconfig.json` file by running the following command:
  ```bash
  npx tsc --init
  ```
- Open the `tsconfig.json` file and set the following options:
  ```json
  "outDir": "./dist",
  "rootDir": "./src"
  ```

#### **4. Test TypeScript Functionality**

- Modify the `server.ts` file to include a simple TypeScript function:

  ```typescript
  // src/server.ts
  const greet = (name: string): string => {
    return `Hello, ${name}!`;
  };

  console.log(greet("World"));
  ```

#### **5. Compile TypeScript**

- Compile the TypeScript files into JavaScript by running:
  ```bash
  npx tsc
  ```
- Verify that a `dist` folder is created containing the compiled JavaScript files.

#### **6. Install Type Definitions**

- Install type definitions for Node.js:
  ```bash
  npm i -D @types/node
  ```

#### **7. Test the Setup**

- Run the compiled JavaScript file to ensure everything works:
  ```bash
  node dist/server.js
  ```

At this point, your project is configured to use TypeScript, with a separate folder (`dist`) for compiled JavaScript files and a sample TypeScript function for testing.

---

## **Step 5: Prettier Setup**

Prettier is a code formatter that ensures consistent code style across your project. Always refer to the [official documentation](https://prettier.io/docs/en/) for the latest updates, as these steps may change in the future.

### **Steps**

#### **1. Install Prettier**

Install Prettier as a development dependency in your project:

```bash
npm install --save-dev --save-exact prettier
```

#### **2. Create a Prettier Configuration File**

Create an empty `.prettierrc` configuration file:

```bash
node --eval "fs.writeFileSync('.prettierrc','{}\n')"
```

#### **3. Create a Prettier Ignore File**

Create a `.prettierignore` file to specify files and directories that Prettier should ignore:

```bash
node --eval "fs.writeFileSync('.prettierignore','# Ignore artifacts:\nbuild\ncoverage\n')"
```

#### **4. Format All Files with Prettier**

Run Prettier to format all files in your project:

```bash
npx prettier . --write
```

#### **5. Add Prettier Scripts to `package.json`**

Add the following scripts to your `package.json` file:

```json
"scripts": {
  "format:fix": "prettier . --write",
  "format:check": "prettier . --check"
}
```

### 6. Install Prettier Extension for VS Code

For a better developer experience, install the [Prettier extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) in VS Code. This allows automatic formatting on file save.

### **Outcome**

At the end of this setup:

- Prettier will format your code according to its default or customized rules.
- Ignored files and folders will not be formatted.
- You can format or check the code style using npm scripts.
- Code consistency is maintained across the project.

---

## **Step 6: ESLint Setup**

ESLint is a static code analysis tool used to identify and fix problematic patterns in JavaScript code. It helps maintain code quality and ensures consistency across the project.

Always refer to the [official documentation](https://typescript-eslint.io/getting-started) for the latest updates.

### **Steps**

#### **1. Installation**

Install the necessary packages:

```bash
npm install --save-dev eslint @eslint/js typescript typescript-eslint
```

#### **2. Configuration**

Create an `eslint.config.mjs` file in the root of your project and populate it with the following:

```javascript
// @ts-check

import eslint from "@eslint/js";
import tseslint from "typescript-eslint";

export default tseslint.config(
  eslint.configs.recommended,
  tseslint.configs.recommended
);
```

#### **3. Running ESLint**

Run ESLint to analyze your code:

```bash
npx eslint .
```

#### **4. Linting with Type Information**

To leverage TypeScript's type checking capabilities for deeper insights, update your `eslint.config.mjs` file as follows:

```javascript
// @ts-check

import eslint from "@eslint/js";
import tseslint from "typescript-eslint";

export default tseslint.config(
  eslint.configs.recommended,
  tseslint.configs.recommendedTypeChecked,
  {
    ignores: ["dist", "node_modules", "eslint.config.mjs"],
  },
  {
    languageOptions: {
      parserOptions: {
        projectService: true,
        tsconfigRootDir: import.meta.dirname,
      },
    },
    rules: {
      // "no-console": "error",
      // "dot-notation": "error",
    },
  }
);
```

#### **5. Install ESLint Extension for VS Code**

Install the [ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) in VS Code to enable automatic linting and error detection.

#### **6. Test ESLint**

Test ESLint to ensure it's working as expected by running some rules:

```bash
npx eslint .
```

### **Outcome**

At the end of this setup:

- ESLint will analyze your code for syntax and style issues.
- You can use TypeScript's type checking for deeper code analysis.
- VS Code will highlight linting errors automatically.
- The project will adhere to consistent coding standards.

---

## **Step 7: Git Hooks Setup**

Git hooks are custom scripts that are triggered automatically by specific events in the Git lifecycle. They allow developers to automate tasks, enforce rules, and customize workflows when working with Git repositories. Hooks can be used for activities like checking code formatting, running tests, or preventing commits that don’t meet certain criteria.

### **Examples of Git Hooks**

- **`pre-commit`**: Runs before a commit is made. Often used to check code formatting or run linters.
- **`commit-msg`**: Runs after writing a commit message but before finalizing the commit. Used to validate commit message formatting.
- **`post-merge`**: Runs after a git merge is completed, useful for reinitializing a project or notifying team members.

---

### **Configuring Git Hooks with Husky**

To simplify the setup and management of Git hooks, we will use **Husky**. Husky is a popular tool for managing Git hooks in JavaScript projects.

Always refers a official documentation as setup may be change in future. [Official Husky Documentation.](https://typicode.github.io/husky/get-started.html)

#### **Step 1: Install Husky**

Run the following command to install Husky as a dev dependency:

```bash
npm install --save-dev husky
```

#### **Step 2: Initialize Husky**

Initialize Husky in your project. This command sets up the necessary files and directories for Husky:

```bash
npx husky init
```

#### **Step 3: Add Pre-Commit Hook**

Add the following script to the `pre-commit` hook file located in the `.husky` directory:

```bash
npm run lint:fix
```

This hook will automatically fix linting errors before committing code.

#### **Step 4: Test the Setup**

To verify that Husky and the Git hooks are working correctly, create a commit:

```bash
git commit -m "add husky"
```

If everything is set up properly, the pre-commit hook will run and execute the linting task.

---

### **Conclustion**

By using Git hooks and tools like Husky, you can enforce better code quality and streamline your development workflow. This setup ensures that your team adheres to coding standards and avoids committing broken or improperly formatted code.

---

## **Setting up lint-staged**

Lint-staged is a tool that allows you to run linters or other scripts only on the files that are staged for commit in a Git repository.

#### **Step 1: Install lint-staged**

To install lint-staged in the recommended way, you need to:

```bash
npm install --save-dev lint-staged
```

#### **Step 2: Configuration**

Add this code to your `package.json` file:

```json
 "lint-staged": {
    "*.ts": [
      "npm run format:fix",
      "npm run lint:fix"
    ]
  }
```

#### **Step 3: Add script to pre-commit**

Add the following script to the `pre-commit` hook file located in the `.husky` directory:

```bash
npx lint-staged
```

This hook will automatically run the code which is added in `package.json` file and run format:fix and lint:fix script.

#### **Step 4: Test the Setup**

To verify that lint-staged are working correctly, run a command:

```bash
npx lint-staged
```

If everything is set up properly, then command will run and execute the formatting and linting task.

---

## **Step - 8 Application Config Setup**

Application configuration helps manage sensitive data like API keys, ports, and environment-specific settings securely and efficiently. Using the `dotenv` package, we can load these settings from a `.env` file.

---

### **Setup Guide**

#### **1. Install `dotenv` package**

Run the following command to install the `dotenv` package:

```bash
npm i dotenv
```

#### **2. Create a `config` folder**

- Inside the `src` directory, create a folder named `config`.
- Inside the `config` folder, create a file named `index.ts`.

#### **3. Configure `dotenv` in `index.ts`**

Add the following code to `index.ts`:

```javascript
import { config } from "dotenv";
config();

const { PORT } = process.env;

export const Config = {
  PORT,
};
```

This code initializes `dotenv` and extracts the `PORT` variable from the `.env` file.

#### **4. Create a `.env` file**

- At the root of your project, create a `.env` file.
- Add the following content:

```
PORT=5501
```

You can replace `5501` with any port number of your choice.

### **Testing the Configuration**

1. Ensure that the `.env` file is at the root of your project.
2. Import the `Config` object from the `config/index.ts` file wherever needed in your application.
3. Access the `PORT` value using `Config.PORT` to confirm the setup works as expected.

Example usage:

```javascript
import { Config } from "./config";

console.log(`Server is running on port: ${Config.PORT}`);
```

Run the application, and it should display the port number defined in the `.env` file.

---

## **Step - 9: Express App Setup**

#### **1. Install Express Package**

Install the `express` package to create the server:

```bash
npm install express
```

#### **2. Create the `app.ts` File**

Inside the `src` folder, create a file named `app.ts` to set up the server:

```javascript
import express from "express";

const app = express();

app.get("/", (req, res) => {
  res.send("Welcome to auth service");
});

export default app;
```

#### **3. Listen to the Express App in `server.ts`**

In the `src` folder, create a `server.ts` file and use it to start the server:

```javascript
import app from "./app";
import { Config } from "./config";

const startServer = () => {
  const PORT = Config.PORT;
  try {
    app.listen(PORT, () => {
      console.log(`Server is running on port ${PORT}`);
    });
  } catch (error) {
    console.error(error);
    process.exit(1);
  }
};

startServer();
```

#### **4. Update the Development Script**

Update the `dev` script in your `package.json` file to use `nodemon` and `ts-node`:

```json
"dev": "nodemon src/server.ts"
```

## **5. Install Additional Packages**

Make sure to install `nodemon` and `ts-node` as these are used by `nodemon` to run TypeScript files:

```bash
npm install --save-dev nodemon ts-node
```

---

## **Step - 10 Logger Setup**

### **What is a Logger?**

A logger is a tool used in software development to record log messages from an application. Logs can help developers monitor the state and flow of an application, debug errors, and analyze performance issues.

---

### **Why Use a Logger?**

- **Debugging**: Helps trace and fix issues in code by providing detailed information.
- **Monitoring**: Tracks application behavior and usage patterns.
- **Error Handling**: Captures errors for analysis and resolution.
- **Audit**: Maintains a record of activities for compliance and auditing purposes.

---

### **Why Not Use console.log in Production?**

- **Performance Overhead**: Blocks the event loop as it’s synchronous, potentially impacting performance.
- **Lack of Features**: Does not support log levels, structured output, or metadata like timestamps.
- **Scalability Issues**: Not suitable for centralized logging or integration with monitoring tools.
- **Unstructured Logs**: Makes it harder to parse and analyze log data.
- **Security Risks**: May accidentally expose sensitive information.

---

### **Why Use Winston for Logging?**

**Winston** is a Node.js logging library designed to be highly flexible and feature-rich.

### **Features of Winston**

- **Log Levels**: Define log severity like info, warn, error.
- **Multiple Transports**: Write logs to console, files, databases, or external services.
- **Structured Logs**: Add metadata, timestamps, and custom formats.
- **Log Rotation**: Automatically manage log file sizes or archive logs.
- **Integration**: Compatible with log management tools like ELK Stack, Splunk, etc.

---

### **Step-by-Step Guide to Setup a Logger**

#### **1. Install Winston**

```bash
npm install winston
```

#### **2. Create a Logger Configuration File**

Create a logger.ts file inside the config folder in src directory.

```typescript
import winston from "winston";

const logger = winston.createLogger({
  level: "info",
  defaultMeta: { serviceName: "auth-service" },
  transports: [
    new winston.transports.File({
      dirname: "logs",
      filename: "combined.log",
      level: "info",
      format: winston.format.combine(
        winston.format.timestamp(),
        winston.format.json()
      ),
      silent: Config.NODE_ENV === "test",
    }),
    new winston.transports.File({
      dirname: "logs",
      filename: "error.log",
      level: "error",
      format: winston.format.combine(
        winston.format.timestamp(),
        winston.format.json()
      ),
      silent: Config.NODE_ENV === "test",
    }),
    new winston.transports.Console({
      level: "info",
      format: winston.format.combine(
        winston.format.timestamp(),
        winston.format.json()
      ),
      silent: Config.NODE_ENV === "test",
    }),
  ],
});

export default logger;
```

### **3. Use the Logger in Your Application**

Replace console.log with Winston's logger for better logging.

#### **Example Usage**

```typescript
import logger from "./logger";

logger.info("Application started successfully.");
logger.warn("This is a warning message.");
logger.error("An unexpected error occurred.");
```

### **6. Test Your Logger**

Run the application and verify logs in both the console and log files:

```bash
node src/server.js
```

---

## **Step - 11 Error Handling Setup**

### **Why a Global Error Handler is Important?**

A global error handler ensures that all errors in your application are handled in a consistent and centralized manner. It helps in:

- **Debugging**: Provides detailed error information to developers.
- **User Experience**: Returns user-friendly error messages instead of exposing technical details.
- **Security**: Prevents leaking sensitive application details in error responses.

---

### **Using `http-errors` Package to Define Errors**

The `http-errors` package is a popular npm library used to create HTTP-friendly error objects. It simplifies defining and handling HTTP errors consistently.

#### **Installation**

Run the following command to install the `http-errors` package:

```bash
npm install http-errors
```

---

#### **Define a Global Error Handler**

Below is the implementation of a global error handler using the `http-errors` package. This will handle errors centrally in your Express app.

#### **Code Implementation**

```typescript
import { Request, Response, NextFunction } from "express";
import { HttpError } from "http-errors";
import logger from "./logger";

app.use((err: HttpError, req: Request, res: Response, next: NextFunction) => {
  logger.error(err.message);

  const statusCode = err.statusCode || 500;

  // Send a structured error response
  res.status(statusCode).json({
    errors: [
      {
        type: err.name,
        msg: err.message,
        path: "",
        location: "",
      },
    ],
  });
});
```

---

### **Testing the Global Error Handler**

1. **Simulate an Error:**
   Add a route to your application that throws an error:

   ```typescript
   app.get("/error", (req, res, next) => {
     const error = new Error("This is a test error");
     next(error);
   });
   ```

2. **Access the Route:**
   Visit `/error` in your browser or using tools like Postman to see the global error handler in action.

3. **Check Logs:**
   Verify that the error is logged using your configured logger.

---

Now your application is equipped with a centralized error-handling mechanism!

---

## **Step - 12 Test Setup**

### **Why Automated Testing is Important**

Automated testing is crucial because:

- **Efficiency**: Saves time by running repetitive tests automatically.
- **Reliability**: Reduces human errors in test execution.
- **Consistency**: Ensures the same tests are run in the same way every time.
- **Scalability**: Handles large test cases for complex applications.
- **Continuous Integration**: Enables seamless integration and deployment workflows.

---

### **Setting Up Automated Tests Using Jest**

#### **What is Jest?**

Jest is a JavaScript testing framework designed to ensure the correctness of any JavaScript codebase. It provides a robust, flexible, and developer-friendly environment for testing.

#### **Types of Testing**

1. **Unit Testing**: Testing individual components or functions.
2. **Integration Testing**: Testing how different parts of an application work together.
3. **End-to-End Testing**: Testing the complete workflow of an application.

---

#### **Installing `Jest`**

```bash
npm install --save-dev jest
```

#### **Add Test Script to `package.json`**

```json
"test": "jest"
```

#### **Installing ts-jest**

Install `ts-jest` to integrate Jest with TypeScript:

```bash
npm install --save-dev ts-jest
```

#### **Why ts-jest?**

`ts-jest` allows Jest to compile and run TypeScript files, ensuring seamless TypeScript support during testing.

#### **Create a Jest Config File**

By default, Jest can run without any config files, but it will not compile `.ts` files. To make it transpile TypeScript with `ts-jest`, create a configuration file:

```bash
npx ts-jest config:init
```

This generates a `jest.config.js` file.

---

### **Create Your First Unit Test**

#### **Create a `utils.ts` File**

Add the following code to `src/utils.ts`:

```typescript
export const calculateDiscount = (price: number, percentage: number) => {
  return price * (percentage / 100);
};
```

#### **Create a `app.spec.ts` File**

Add the following test code to `app.spec.ts`:

```typescript
import { calculateDiscount } from "./src/utils";

// Test suite
describe("App", () => {
  it("should return correct discount amount", () => {
    const discount = calculateDiscount(100, 10);
    expect(discount).toBe(10);
  });
});
```

Run the test using:

```bash
npm test
```

---

## **Install Supertest**

### **What is Supertest?**

Supertest is a library used for HTTP assertions. It allows developers to test HTTP endpoints seamlessly.

#### **Install Supertest**

```bash
npm install supertest --save-dev
```

---

### **Create an HTTP Endpoint Test**

#### **Test Code**

Add the following test code to `app.spec.ts`:

```typescript
import app from "./src/app";
import request from "supertest";

// Test suite
describe("App", () => {
  it("should return 200 status code", async () => {
    const response = await request(app).get("/").send();
    expect(response.statusCode).toBe(200);
  });
});
```

Run the test using:

```bash
npm test
```

---

Now your project is set up for automated testing with Jest and Supertest!

---
