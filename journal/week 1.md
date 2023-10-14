# Week 1

## Setting up the project

```zsh
npx create-next-app@latest
```

`project name : . ` This will direct the package manager to install the project as if the folder is the project folder rather than create the new project folder within the folder.
select yes for all except for `src/` directory and alias.

### Setting up eslint and prettier

[link](/journal/project%20linting%20and%20prettier.md)

## Setting up tailwindcss and style guide

updated [tailwind.config.ts](/tailwind.config.ts)

```ts
// folder in root directory
/** @type {import('tailwindcss').Config} */
module.exports = {
  darkMode: ["class"],
  content: [
    "./pages/**/*.{ts,tsx}",
    "./components/**/*.{ts,tsx}",
    "./app/**/*.{ts,tsx}",
    "./src/**/*.{ts,tsx}",
  ],
  theme: {
    container: {
      center: true,
      padding: "2rem",
      screens: {
        "2xl": "1400px",
      },
    },
    extend: {
      colors: {
        primary: {
          500: "#FF7000",
          100: "#FFF1E6",
        },
        dark: {
          100: "#000000",
          200: "#0F1117",
          300: "#151821",
          400: "#212734",
          500: "#101012",
        },
        light: {
          900: "#FFFFFF",
          800: "#F4F6F8",
          850: "#FDFDFD",
          700: "#DCE3F1",
          500: "#7B8EC8",
          400: "#858EAD",
        },
        "accent-blue": "#1DA1F2",
      },
      fontFamily: {
        inter: ["var(--font-inter)"],
        spaceGrotesk: ["var(--font-spaceGrotesk)"],
      },
      boxShadow: {
        "light-100":
          "0px 12px 20px 0px rgba(184, 184, 184, 0.03), 0px 6px 12px 0px rgba(184, 184, 184, 0.02), 0px 2px 4px 0px rgba(184, 184, 184, 0.03)",
        "light-200": "10px 10px 20px 0px rgba(218, 213, 213, 0.10)",
        "light-300": "-10px 10px 20px 0px rgba(218, 213, 213, 0.10)",
        "dark-100": "0px 2px 10px 0px rgba(46, 52, 56, 0.10)",
        "dark-200": "2px 0px 20px 0px rgba(39, 36, 36, 0.04)",
      },
      backgroundImage: {
        "auth-dark": "url('/assets/images/auth-dark.png')",
        "auth-light": "url('/assets/images/auth-light.png')",
      },
      screens: {
        xs: "420px",
      },
      keyframes: {
        "accordion-down": {
          from: { height: 0 },
          to: { height: "var(--radix-accordion-content-height)" },
        },
        "accordion-up": {
          from: { height: "var(--radix-accordion-content-height)" },
          to: { height: 0 },
        },
      },
      animation: {
        "accordion-down": "accordion-down 0.2s ease-out",
        "accordion-up": "accordion-up 0.2s ease-out",
      },
    },
  },
  plugins: [require("tailwindcss-animate"), require("@tailwindcss/typography")],
};
```

created a new folder `styles` and within it create `theme.css`
updated [theme.css](/styles/theme.css)

```css
/* file in styles/theme.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer utilities {
  .background-light850_dark100 {
    @apply bg-light-850 dark:bg-dark-100;
  }

  .background-light900_dark200 {
    @apply bg-light-900 dark:bg-dark-200;
  }

  .background-light900_dark300 {
    @apply bg-light-900 dark:bg-dark-300;
  }

  .background-light800_darkgradient {
    @apply bg-light-800 dark:dark-gradient;
  }

  .background-light800_dark400 {
    @apply bg-light-800 dark:bg-dark-400 !important;
  }

  .background-light700_dark400 {
    @apply bg-light-700 dark:bg-dark-400;
  }

  .background-light700_dark300 {
    @apply bg-light-700 dark:bg-dark-300;
  }

  .background-light800_dark400 {
    @apply bg-light-800 dark:bg-dark-400;
  }

  .background-light800_dark300 {
    @apply bg-light-800 dark:bg-dark-300 !important;
  }

  .text-dark100_light900 {
    @apply text-dark-100 dark:text-light-900 !important;
  }

  .text-dark200_light900 {
    @apply text-dark-200 dark:text-light-900;
  }

  .text-dark200_light800 {
    @apply text-dark-200 dark:text-light-800 !important;
  }

  .text-dark300_light700 {
    @apply text-dark-300 dark:text-light-700;
  }

  .text-dark400_light700 {
    @apply text-dark-400 dark:text-light-700;
  }

  .text-dark500_light700 {
    @apply text-dark-500 dark:text-light-700 !important;
  }

  .text-dark500_light500 {
    @apply text-dark-500 dark:text-light-500;
  }

  .text-dark300_light900 {
    @apply text-dark-300 dark:text-light-900 !important;
  }

  .text-dark400_light800 {
    @apply text-dark-400 dark:text-light-800;
  }

  .text-light400_light500 {
    @apply text-light-400 dark:text-light-500 !important;
  }

  .text-dark400_light500 {
    @apply text-dark-400 dark:text-light-500;
  }

  .text-dark400_light900 {
    @apply text-dark-400 dark:text-light-900 !important;
  }

  .text-light400_light500 {
    @apply text-light-400 dark:text-light-500 !important;
  }

  .light-border {
    @apply border-light-800 dark:border-dark-300;
  }

  .light-border-2 {
    @apply border-light-700 dark:border-dark-400 !important;
  }

  .h1-bold {
    @apply text-[30px] font-bold leading-[42px] tracking-tighter;
  }

  .h2-bold {
    @apply text-[24px] font-bold leading-[31.2px];
  }

  .h2-semibold {
    @apply text-[24px] font-semibold leading-[31.2px];
  }

  .h3-bold {
    @apply text-[20px] font-bold leading-[26px];
  }

  .h3-semibold {
    @apply text-[20px] font-semibold leading-[24.8px];
  }

  .base-medium {
    @apply text-[18px] font-medium leading-[25.2px];
  }

  .base-semibold {
    @apply text-[18px] font-semibold leading-[25.2px];
  }

  .base-bold {
    @apply text-[18px] font-bold leading-[140%];
  }

  .paragraph-regular {
    @apply text-[16px] font-normal leading-[22.4px];
  }

  .paragraph-medium {
    @apply text-[16px] font-medium leading-[22.4px];
  }

  .paragraph-semibold {
    @apply text-[16px] font-semibold leading-[20.8px];
  }

  .body-regular {
    @apply text-[14px] font-normal leading-[19.6px];
  }

  .body-medium {
    @apply text-[14px] font-medium leading-[18.2px];
  }

  .body-semibold {
    @apply text-[14px] font-semibold leading-[18.2px];
  }

  .small-regular {
    @apply text-[12px] font-normal leading-[15.6px];
  }

  .small-medium {
    @apply text-[12px] font-medium leading-[15.6px];
  }

  .small-semibold {
    @apply text-[12px] font-semibold leading-[15.6px];
  }

  .subtle-medium {
    @apply text-[10px] font-medium leading-[13px] !important;
  }

  .subtle-regular {
    @apply text-[10px] font-normal leading-[13px];
  }

  .placeholder {
    @apply placeholder:text-light-400 dark:placeholder:text-light-500;
  }

  .invert-colors {
    @apply invert dark:invert-0;
  }

  .shadow-light100_dark100 {
    @apply shadow-light-100 dark:shadow-dark-100;
  }

  .shadow-light100_darknone {
    @apply shadow-light-100 dark:shadow-none;
  }

  .primary-gradient {
    background: linear-gradient(129deg, #ff7000 0%, #e2995f 100%);
  }

  .dark-gradient {
    background: linear-gradient(
      232deg,
      rgba(23, 28, 35, 0.41) 0%,
      rgba(19, 22, 28, 0.7) 100%
    );
  }
}
```

update `app/globals.css` [globals.css](/app/globals.css)

```css
/* folder in app/globals.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

@import url("../styles/theme.css");

body {
  font-family: "Inter", sans-serif;
}

@layer utilities {
  .flex-center {
    @apply flex justify-center items-center;
  }

  .flex-between {
    @apply flex justify-between items-center;
  }

  .flex-start {
    @apply flex justify-start items-center;
  }

  .card-wrapper {
    @apply bg-light-900 dark:dark-gradient shadow-light-100 dark:shadow-dark-100;
  }

  .btn {
    @apply bg-light-800 dark:bg-dark-300 !important;
  }

  .btn-secondary {
    @apply bg-light-800 dark:bg-dark-400 !important;
  }

  .btn-tertiary {
    @apply bg-light-700 dark:bg-dark-300 !important;
  }

  .markdown {
    @apply max-w-full prose dark:prose-p:text-light-700 dark:prose-ol:text-light-700 dark:prose-ul:text-light-500 dark:prose-strong:text-white dark:prose-headings:text-white prose-headings:text-dark-400 prose-h1:text-dark-300 prose-h2:text-dark-300 prose-p:text-dark-500 prose-ul:text-dark-500 prose-ol:text-dark-500;
  }

  .primary-gradient {
    background: linear-gradient(129deg, #ff7000 0%, #e2995f 100%);
  }

  .dark-gradient {
    background: linear-gradient(
      232deg,
      rgba(23, 28, 35, 0.41) 0%,
      rgba(19, 22, 28, 0.7) 100%
    );
  }

  .tab {
    @apply min-h-full dark:bg-dark-400 bg-light-800 text-light-500 dark:data-[state=active]:bg-dark-300 data-[state=active]:bg-primary-100 data-[state=active]:text-primary-500 !important;
  }
}

.no-focus {
  @apply focus-visible:ring-0 focus-visible:ring-transparent focus-visible:ring-offset-0 !important;
}

.active-theme {
  filter: invert(53%) sepia(98%) saturate(3332%) hue-rotate(0deg) brightness(
      104%
    ) contrast(106%) !important;
}

.light-gradient {
  background: linear-gradient(
    132deg,
    rgba(247, 249, 255, 0.5) 0%,
    rgba(229, 237, 255, 0.25) 100%
  );
}

.primary-text-gradient {
  background: linear-gradient(129deg, #ff7000 0%, #e2995f 100%);
  background-clip: text;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.custom-scrollbar::-webkit-scrollbar {
  width: 3px;
  height: 3px;
  border-radius: 2px;
}

.custom-scrollbar::-webkit-scrollbar-track {
  background: #ffffff;
}

.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 50px;
}

.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #555;
}

/* Markdown Start */
.markdown a {
  color: #1da1f2;
}

.markdown a,
code {
  /* These are technically the same, but use both */
  overflow-wrap: break-word;
  word-wrap: break-word;

  -ms-word-break: break-all;
  /* This is the dangerous one in WebKit, as it breaks things wherever */
  word-break: break-all;
  /* Instead use this non-standard one: */
  word-break: break-word;

  /* Adds a hyphen where the word breaks, if supported (No Blink) */
  -ms-hyphens: auto;
  -moz-hyphens: auto;
  -webkit-hyphens: auto;
  hyphens: auto;

  padding: 2px;
  color: #ff7000 !important;
}

.markdown pre {
  display: grid;
  width: 100%;
}

.markdown pre code {
  width: 100%;
  display: block;
  overflow-x: auto;

  color: inherit !important;
}
/* Markdown End */

/* Clerk */
.cl-internal-b3fm6y {
  background: linear-gradient(129deg, #ff7000 0%, #e2995f 100%) !important;
}

.hash-span {
  margin-top: -140px;
  padding-bottom: 140px;
  display: block;
}

/* Hide scrollbar for Chrome, Safari and Opera */
.no-scrollbar::-webkit-scrollbar {
  display: none;
}

/* Hide scrollbar for IE, Edge and Firefox */
.no-scrollbar {
  -ms-overflow-style: none; /* IE and Edge */
  scrollbar-width: none; /* Firefox */
}
```

## Setting up folder structure

[Setting up folder structure](https://courses.jsmastery.pro/course/ultimate-next-js-13-course-ebook/learn/module-setup/code-architecture)

### added `.vscode` in root directory for custom vs code settings

```json
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

### added `lib/actions`

The "lib\actions" folder in a project is typically used to store code or scripts related to specific actions or operations with backend or 3rd party service providers. It's a common convention to organize project files and code into specific directories for better maintainability.
The "lib" directory is short for "library" and often contains reusable code or functions that are commonly used throughout the project. The "actions" subdirectory within "lib" is specifically dedicated to code files related to actions or operations performed by the project.
By storing action-specific code in the "lib\actions" folder, developers can easily locate and manage the code responsible for implementing specific functionalities or tasks within the project. It promotes modular and organized development practices.

```python
# File: lib\actions\email_actions.py
def send_email(recipient, subject, body):
    # Code to send an email to the recipient with the given subject and body
    # ...
    pass

def delete_email(email_id):
    # Code to delete an email with the given ID
    # ...
    pass
```

In this example, the "lib\actions\email_actions.py" file contains functions related to email actions, specifically sending emails and deleting emails. These functions encapsulate the logic and operations required to perform these actions within the project.
By organizing these email-related actions in the "lib\actions" folder, it becomes easier for developers to locate, manage, and maintain the code responsible for email-related tasks separately from other parts of the project. Other code files in different directories (such as "lib\controllers" or "lib\utilities") can then use or call these functions from the actions library appropriately, promoting code reusability and separation of concerns.

### added `.env.local` file

storing of the environmnet variables that can be sensitive to push to code repositive.

### added`components` folder

Storing of resuable components. Aligning with the DRY principle.

### added `constants` folder

Storing of resuable contants that we will use in the project.
example below for navigation bar.

```json
[
  {
    "text": "Home",
    "link": "/home"
  },
  {
    "text": "About",
    "link": "/about"
  },
  {
    "text": "Services",
    "link": "/services"
  },
  {
    "text": "Contact",
    "link": "/contact"
  }
]
```

### added `context` folder

for theme provider

### added `database` folder

To store data schema/model

### added `types` folder

To store typescript types.

## Next.js Routing

In Next.js' file-based routing system, the folders within the "pages" directory play a significant role in defining the routing behavior and creating nested routes for your application.
When you create a folder with a specific name inside the "pages" directory, it represents a nested route in your application. The folder's name corresponds to a segment in the URL path, and any files placed within that folder become accessible as nested routes under that segment.
For example, if you have a folder named "products" within the "pages" directory, with a file named "index.js" inside it, the resulting URL path for that page would be "/products". Additionally, if you create another file named "shoes.js" within the "products" folder, it would be accessible at the "/products/shoes" route.
This hierarchical structure allows you to create nested routes and organize your application's pages logically. It is particularly useful for building complex applications with multiple levels of routes, such as e-commerce sites with category pages and product details pages.
By leveraging the folder structure in Next.js, you can create a clean and intuitive routing system that reflects the structure of your application and improves maintainability.
