# Setup ESLint & Prettier in VS Code

## Introduction to Linting, ESLint, and Prettier

Linting is the process of analyzing code for potential errors, bugs, and stylistic issues. It helps maintain a consistent code style, improves code quality, and catches common mistakes early in development. Two popular tools for linting modern web development code are ESLint and Prettier.

### What is Prettier?

Prettier is a code formatter that focuses on code formatting and style consistency. It automatically formats your code according to predefined rules, making it more readable and eliminating debates over code style.

A **code formatter** is primarily concerned with the visual appearance and consistent code formatting. It automatically analyzes the structure of the code and applies predefined formatting rules to ensure a uniform style throughout the codebase. Code formatters focus on aspects such as indentation, line breaks, spacing, and the placement of braces and parentheses. The goal of a code formatter like Prettier is to standardize the appearance of code, making it more readable and enhancing code consistency within a project or team.

### What is ESLint?

ESLint is a linter that allows you to define custom linting rules and enforce coding standards. It helps identify and fix potential errors, enforces consistent coding styles, and promotes best practices in your codebase.

A **code linter** goes beyond code formatting and focuses on the correctness, quality, and potential issues within the code. Linters analyze the code for potential errors, bugs, stylistic inconsistencies, and violations of coding standards and best practices. They check for issues such as unused variables, missing semicolons, incorrect function usage, possible memory leaks, and adherence to coding conventions. Code linters like ESLint provide warnings, errors, or suggestions to developers about problematic code areas, helping them identify and fix potential issues early in the development process. By enforcing consistent coding styles and detecting errors, linters improve code quality and maintainability and reduce the likelihood of bugs.

### Best of Both Worlds

Combining ESLint and Prettier in your development workflow can greatly improve code quality, maintainability, and collaboration within a team. ESLint ensures your code adheres to specific rules and catches potential issues, while Prettier enforces consistent code formatting.

With ESLint and Prettier configured in your development environment, you can focus on writing clean, high-quality code while enjoying automated code formatting and helpful linting feedback.

Let's get started!

## Next.js 13 Setup

Use `npx create next-app@latest`. Select yes when asked about adding ESLint to your project:

![Screenshot 2023-07-11 at 10.28.39 PM.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9dd35091-8d1d-4ac0-a111-2b2639543480/Screenshot_2023-07-11_at_10.28.39_PM.png)

Once this is done, open up the project in VSCode.

### Add an ESLint Config

If you look at the \*`.eslintrc.json` **\***file at the root of your new Next.js project, you’ll see that there is already an ESLint configuration called **_next/core-web-vitals_** and **********\*\*\*\***********standard**********\*\*\*\***********. It’s important to keep it. It will warn you when you write code in your Next.js project that affects core web vitals.

We still need to add another ESLint configuration for consistent code styling, as the default Next configuration doesn’t do much to help you improve the quality of your codebase.

Let’s install the standard configuration. Here are its [rules](https://standardjs.com/rules.html).

> _Protip: learning the rules will allow you to improve your code quality immediately._

Now, run:

```bash
npm install eslint-config-standard
```

This will install the standard ESLint configuration in your project. Then, add it to your `**.eslintrc.json**` file:

```jsx
{
  "extends": ["next/core-web-vitals", "standard"]
}
```

### Testing ESLint in the Terminal

Now that we have added a new ESLint configuration let’s run it with

```bash
npm run lint
```

to ensure it’s working. Later on, I’ll show you how to get it to work in VSCode automatically as soon as you save a file.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7ed44a07-5a81-47b3-b2bf-bb609e2b1cb7/Untitled.png)

Here you see a bunch of errors. Exactly what we needed 😅.

For example, the standard code style wants us to use single quotes rather than double quotes for strings.

### Adding an ESLint Configuration for TailwindCSS

Having our class names organized logically in Tailwind makes the code easier to read and review. We can install another ESLint config that takes care of that to do this automatically.

Run:

```bash
npm install eslint-plugin-tailwindcss ****
```

and add it to your **`.eslintrc.json`** file like this:

```jsx
{
  "extends": ["next/core-web-vitals", "standard", "plugin:tailwindcss/recommended"]
}
```

### Prettier VS ESLint potential conflicts

ESLint sometimes likes to enter into conflict with Prettier. 🥊

To avoid these situations, you should run:

```bash
npm install eslint-config-prettier
```

This will install a package that removes all ESLint rules that could conflict with Prettier. Once installed, add “prettier” to your `**.eslintrc.json**` file.

```jsx
{
  "extends": ["next/core-web-vitals", "standard", "plugin:tailwindcss/recommended", "prettier"]
}
```

## Install Prettier

Don’t forget to install prettier before proceeding; otherwise, things will not work, and you won’t know why. 🤷

Run:

```bash
npm install prettier
```

### Setting things up for VSCode

Now that everything is set up command-line-wise, it’s time to integrate ESLint and Prettier with VSCode. For that, we will need to modify the `**settings.json**` file or create a config specific to our project that you can share with others if you’d like. We’ll go with the latter.

In your Next.js project at the root, create a `**.vscode`** folder and within it a `**settings.json\*\*` file with the following code:

```tsx
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true,
    "source.addMissingImports": true
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

This sets up ESlint and Prettier to work within VSCode. Every time you hit save, both Prettier and ESLint will run. But to test it in action, there’s one final thing we have to do…

### Install ESLint and Prettier from the Extensions Marketplace

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc45cfa0-5b4e-47ff-bb9d-58d0d1c1a826/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/76add50d-0622-40c7-8cf6-4f63601d383e/Untitled.png)

Once both are installed, restart your Visual Studio Code. Now try to edit and save some files. You should see that Prettier and ESLint are now working. To test that the Tailwind CSS plugin is also working. Try to put flex class names as the last class member and see if it is returned to the front when saving.

![ezgif-3-bc2d11118c.gif](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f64574f2-ed79-4921-b227-26f18752b674/ezgif-3-bc2d11118c.gif)

### Conclusion

You can finally start working on your project rather than pulling your hair out with configurations. 😄
