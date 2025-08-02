# TypeScript Style Guide

## 1. Guiding Principles

- **Strict Mode**: All code is written in TypeScript's `strict` mode to ensure maximum type safety.
- **Type Safety**: Avoid using the `any` type. Always define explicit types or leverage type
  inference.
- **Shared Types**: For consistency between the frontend and backend, we use a dedicated
  `@auth-system/shared-types` package for all shared data structures.

## 2. Naming Conventions

- **Components**: `PascalCase` (e.g., `AuthForm.tsx`)
- **Classes & Services**: `PascalCase` (e.g., `AuthService`)
- **Interfaces**: `PascalCase` with a mandatory `I` prefix (e.g., `IUserRepository`).
- **Variables & Functions**: `camelCase` (e.g., `getUser`)
- **Files**: `kebab-case` for documentation and configuration files, `PascalCase` for component
  files.

## 3. Module Path Aliases

We use specific path aliases to keep imports clean and consistent across the monorepo:

- **`@auth-system/*`**: For importing from other packages within the workspace.
  - **Example**: `import { UserResponse } from '@auth-system/shared-types'`
- **`~/*`**: For imports within the same local workspace (`app` or `package`).
  - **Example**: `import { Button } from '~/components/ui/Button'`

## 4. Code Structure

- **Backend**: Follows a strict **Clean Architecture** pattern, with code organized into `domain`,
  `application`, and `infrastructure` layers.
- **Frontend**: Components are organized by function into directories like `components/ui`,
  `components/forms`, and `components/layouts`.

## 5. Error Handling

We use a layered error-handling strategy to ensure that errors are handled at the appropriate level
of the application.

- **Domain Layer**: Throws custom error classes for business rule violations (e.g.,
  `InvalidEmailError`).
- **Application Layer**: Catches domain errors and either handles them or re-throws them as
  application-specific exceptions.
- **Infrastructure Layer**: Catches all errors and translates them into appropriate HTTP responses.
