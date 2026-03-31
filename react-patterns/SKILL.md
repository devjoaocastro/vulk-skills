---
name: vulk-react-patterns
description: "Correct React patterns for generated code. Always loaded for React projects. Triggers: react, component, hook, state, jsx"
license: MIT
---

# React Patterns -- Canonical Code

## 1. Component Structure
- One component per file, named export matching filename
- Props interface defined above component
- Destructure props in function signature
- Keep components under 200 lines -- extract sub-components

## 2. State Management
- useState for local UI state
- useReducer for complex state with multiple related updates
- Context for theme, auth, cart -- NOT for frequently changing data
- Lift state up only when siblings need it

## 3. Performance
- useMemo for expensive computations (NOT for simple values)
- useCallback for functions passed to memoized children
- React.memo only on components that re-render often with same props
- NEVER premature optimization -- measure first

## 4. Routing (React Router)
- Always use createBrowserRouter for new projects
- Lazy load route components: `const Page = lazy(() => import('./Page'))`
- Wrap lazy routes in Suspense with loading fallback
- Use outlet for nested layouts

## 5. Error Handling
- ErrorBoundary wrapping route sections
- try/catch in async operations
- Loading states for all data fetching
- Empty states that look intentional (not broken)

## 6. File Organization

```
src/
  components/     # Reusable UI components
  pages/          # Route-level components
  hooks/          # Custom hooks
  lib/            # Utilities, API client, constants
  store/          # State management (context/zustand)
  styles/         # Global CSS
```
