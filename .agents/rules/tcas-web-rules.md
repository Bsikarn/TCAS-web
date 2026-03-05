---
trigger: always_on
---

# Project Workspace Rules: TCAS KMUTNB Hub

## 1. Tech Stack Overview
- **Language:** JavaScript (JSX) - **Strictly NO TypeScript (.ts, .tsx)**. Use only `.js` and `.jsx`.
- **Frontend Framework:** React 19
- **Build Tool:** Vite
- **Styling:** Tailwind CSS v4
- **UI Components:** Radix UI / Shadcn UI
- **Routing:** React Router DOM
- **Icons:** Lucide React
- **Backend/Database:** Supabase, Microsoft SQL

## 2. General Code Style & Architecture
- Write clean, readable, and modular code.
- Always use Functional Components. Do not use Class Components.
- Use PascalCase for filenames and React components (e.g., `DashboardCard.jsx`, `UserProfile.jsx`).
- Use camelCase for variables and standard functions (e.g., `fetchUserData`, `isLoggedIn`).
- Since we are using plain JavaScript, utilize JSDoc comments to document types and provide intellisense for the editor.

## 3. React 19 & React Router DOM
- Strictly follow the Rules of Hooks.
- Leverage React 19 features (like Actions or new Form handling) where appropriate.
- **Routing:**
  - Always use `<Link to="...">` from `react-router-dom` for standard link clicks to ensure a seamless Single Page Application (SPA) experience without full-page reloads.
  - Use the `useNavigate()` hook for programmatic navigation (e.g., redirecting after a form submission).

## 4. Styling (Tailwind CSS v4 & Shadcn UI)
- **Tailwind v4:** Follow the v4 CSS-first configuration approach. Avoid complex JavaScript config files unless necessary.
- **Dynamic Classes:** Whenever you need to mix classes or apply conditional styling, **always use the `cn()` utility function** (which utilizes `clsx` and `tailwind-merge`).
  - *Correct Example:* `className={cn("bg-blue-500 p-4", isActive && "bg-blue-700", customClass)}`
- Avoid writing custom vanilla CSS. Rely entirely on Tailwind's utility classes.
- Use Shadcn UI as the foundation. If you need to tweak the design, modify the generated Shadcn component files directly.

## 5. Icons (Lucide React)
- Use `lucide-react` exclusively to maintain a consistent, minimal design and keep the bundle size small.
- *Example:* `import { Calendar, Users, BookOpen } from "lucide-react";`
- Control icon size and color using Tailwind classes (e.g., `className="w-5 h-5 text-gray-500"`) instead of passing inline props whenever possible.

## 6. Backend & Data Fetching (Supabase & MS SQL)
- Separate data fetching logic from UI components. Keep API calls in dedicated directories like `src/services` or `src/lib`.
- Implement robust error handling for all interactions with Supabase and your MS SQL backend.
- Always use Vite environment variables (`import.meta.env.VITE_...`) for API keys, database URLs, and sensitive configuration. Never hardcode them.

## 7. Performance & Optimization
- Be mindful of unnecessary re-renders. Check your dependencies in hooks carefully.
- Lazy load heavy components or large assets if they are not immediately needed on the screen.