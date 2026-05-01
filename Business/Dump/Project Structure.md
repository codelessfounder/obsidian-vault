---

---

**Project Structure**

- **public/**: Likely contains static assets (images, icons, etc.) for the extension.
- **src/**: Main source code directory.
- **components/**: UI components, with a subfolder for reusable UI elements.
- **content/**: Likely contains content scripts injected into web pages.
- **hooks/**: Custom React hooks.
- **lib/**: Utility functions or libraries.
- **pages/**: React page components (e.g., Index, NotFound, browserhome).
- **types/**: TypeScript type definitions.
- **background.js**: Background script for the extension, handling persistent logic.
- **content.js**: Content script, probably injected into e-commerce sites to read cart totals, etc.
- **manifest.json**: Extension manifest, defining permissions, scripts, and metadata.
- **tailwind.config.ts**: Tailwind CSS configuration, indicating use of Tailwind for styling.
- **vite.config.ts**: Vite configuration, suggesting Vite is used as the build tool.
- **package.json**: Project dependencies and scripts.
- **README.md**: Project documentation.

**App Structure (from src/App.tsx)**

- Uses React with React Router for navigation.
- Integrates React Query for data fetching/caching.
- Uses a splash screen (SplashScreen) before showing the main app.
- Provides routes for / (Index), /browserhome (BrowserHome), and a catch-all for 404s (NotFound).
- UI components like Toaster and Sonner for notifications, and TooltipProvider for tooltips.
- The app is structured to be modular and scalable, with clear separation of concerns.

**Design & UX**

- There’s a strong emphasis on consistent UI/UX, with a dedicated UI components folder and Tailwind for design tokens.
- The user rules specify that all new UI must match the existing design system in terms of colors, spacing, typography, and interaction patterns.

**Functionality (inferred from structure and rules)**

- The extension reads the cart total from e-commerce sites (likely via content scripts).
- Prompts users to connect a crypto wallet and place a wager.
- Executes a coin flip, and based on the result, either rewards the user or retains the crypto.
- The user can then proceed with their purchase as normal.

**Technologies Used**

- React (with hooks and router)
- TypeScript
- Tailwind CSS
- Vite (build tool)
- React Query (data fetching)
- Likely uses browser APIs for extension functionality (background/content scripts)
- Possibly uses a crypto wallet integration (e.g., MetaMask, WalletConnect), though not directly visible in the files listed.

---

If you want a deeper dive into specific files, logic, or want a summary of a particular part (e.g., wallet integration, wager logic, UI components), let me know! I can read and summarize any file or folder in detail.

App.tsx

disco-extension

project-statement