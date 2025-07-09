# Vite + React + TypeScript Project Template

This is a robust, scalable, and maintainable template for building modern web applications and Chrome extensions. It uses Vite for a blazing-fast development experience, React for building user interfaces, and TypeScript for type safety.

## Core Philosophy

The project is structured using a **feature-based architecture**. Instead of grouping files by their type (e.g., all components in one folder, all API calls in another), we group them by the feature they belong to. This makes the codebase easier to navigate, scale, and maintain, as all related logic for a specific part of the application is co-located.

## Getting Started

1.  **Navigate to the project directory:**
    ```bash
    cd my-project-template
    ```
2.  **Install dependencies:**
    ```bash
    npm install
    ```
3.  **Start the development server:**
    ```bash
    npm run dev
    ```
    The application will be available at `http://localhost:5173`.

## Available Scripts

**Important:** Make sure you're in the `my-project-template` directory before running these commands.

-   `npm run dev`: Starts the Vite development server with Hot Module Replacement (HMR) enabled.
-   `npm run build`: Bundles the application for production into the `dist` folder.
-   `npm run lint`: Lints the codebase using ESLint.
-   `npm run preview`: Serves the production build locally to preview it.

## Project Structure Explained

```
/
├── public/              # Static assets and the manifest.json
├── src/
│   ├── assets/          # Images, fonts, etc.
│   ├── components/      # Shared, reusable React components
│   │   ├── common/      # Generic UI components (Button, Input, Modal)
│   │   └── layout/      # Page structure components (Header, Footer, Sidebar)
│   ├── features/        # Self-contained application features
│   ├── hooks/           # Global, reusable custom React hooks
│   ├── lib/             # Configuration for third-party libraries (Axios, Firebase)
│   ├── pages/           # Top-level page components that map to routes
│   ├── services/        # Core application-wide services (e.g., API layer)
│   ├── styles/          # Global styles and theme variables
│   ├── types/           # Global TypeScript type definitions
│   ├── utils/           # General utility functions
│   ├── App.tsx          # Main application component with routing
│   └── main.tsx         # The entry point of the application
├── .gitignore
├── index.html           # The HTML entry point for Vite
├── package.json
├── tsconfig.json
└── vite.config.ts
```

### Key Directories

-   **`src/components`**: Contains React components that are shared across different features of the application.
    -   **`common/`**: For highly reusable, "dumb" UI components like `Button`, `Input`, `Card`, etc. These should not contain business logic.
    -   **`layout/`**: For components that define the overall structure of the app, such as `Navbar`, `Sidebar`, and `Footer`.

-   **`src/features`**: The most important directory. Each sub-directory here represents a distinct feature of your application (e.g., `authentication`, `dashboard`, `user-profile`). Each feature folder should contain everything related to that feature: its own components, API calls, hooks, and types.

-   **`src/hooks`**: For custom React hooks that are generic enough to be used across multiple features (e.g., `useLocalStorage`, `useTheme`).

-   **`src/pages`**: Contains components that represent an entire page or view. These components are typically what your router will render. They assemble various layout and feature components to create a complete page.

-   **`src/lib`**: Use this to centralize the configuration of external libraries. For example, an `axios.ts` file here can export a pre-configured instance for making API calls.

-   **`src/services`**: For core services that are fundamental to the application's operation, such as a centralized API service or an analytics service.

-   **`src/utils`**: A place for pure, helper functions that are not tied to React or any specific feature (e.g., date formatting, string manipulation, validation functions).

## Chrome Extension Development

This template is pre-configured for Chrome Extension development.

-   The `public/manifest.json` file is the heart of your extension.
-   The `default_popup` is set to `index.html`, which means your entire React application will render in the extension's popup.
-   To load the extension for testing, run `npm run build` (from the `my-project-template` directory) and load the generated `dist` directory as an "unpacked extension" in Chrome's `chrome://extensions` page.
