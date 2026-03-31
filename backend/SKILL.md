---
name: vulk-backend
description: "PostgreSQL schema, auth patterns, API design for full-stack generation. Triggers: backend, database, auth, login, register, api, postgresql, sql, crud, admin, dashboard"
license: MIT
---

# Backend and Database -- Full-Stack Patterns

## 1. Schema Design (schema.sql)
- Always include: id (UUID), created_at, updated_at
- Use snake_case for columns
- Foreign keys with ON DELETE CASCADE where appropriate
- Indexes on frequently queried columns
- NEVER store plain passwords -- use password_hash column
- Include role column on users table: 'user' | 'admin' | 'editor'

## 2. Seed Data (seed.sql)
- Insert realistic data, NOT lorem ipsum
- At least 5-10 rows per table
- Use fixed dates (not NOW()) for reproducibility
- Include an admin user with known credentials
- Demo credentials: admin@demo.com / demo123 (document in UI)

## 3. Auth Pattern (AuthContext)

```tsx
// Store: zustand or context
interface AuthState {
  user: User | null;
  token: string | null;
  login: (email: string, password: string) => Promise<void>;
  register: (data: RegisterData) => Promise<void>;
  logout: () => void;
  isAuthenticated: boolean;
}
// Protected route wrapper
function ProtectedRoute({ children }) {
  const { isAuthenticated } = useAuth();
  if (!isAuthenticated) return <Navigate to="/login" />;
  return children;
}
```

## 4. API Client (api.ts)
- Single axios/fetch instance with base URL
- Auto-attach auth token from localStorage
- Interceptor for 401 redirect to login
- Type-safe response handling
- Base URL: the VULK API Engine backend URL

## 5. Admin Panel Pattern
- Sidebar navigation with sections
- Dashboard with stat cards (total users, revenue, etc.)
- CRUD tables with search, filter, pagination
- Detail views with edit forms
- Confirmation dialogs for destructive actions
