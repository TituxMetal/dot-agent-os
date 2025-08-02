# System Patterns

## 1. High-Level Architecture

Our architecture is built on a **monorepo** foundation, managed with **Yarn workspaces** and
optimized with **Turbo**. This structure supports a full-stack application with a clear separation
between the frontend and backend.

- **Backend**: A **NestJS** application built with **Clean Architecture** and **Domain-Driven Design
  (DDD)** principles.
- **Frontend**: A hybrid application using **Astro** for static content and **React** for
  interactive "islands of interactivity."

## 2. Backend Patterns

The backend follows a strict implementation of Clean Architecture, with three distinct layers:

1. **Domain Layer**: Contains the core business logic, entities, and value objects. This layer is
   completely independent of any framework or external dependency.
2. **Application Layer**: Orchestrates the use cases of the application, acting as a bridge between
   the domain and infrastructure layers.
3. **Infrastructure Layer**: Handles all external concerns, such as database interactions (with
   **Prisma**), web controllers, and third-party services.

**Key Principles**:

- **Dependency Rule**: Dependencies flow inwards. The infrastructure layer depends on the
  application layer, which in turn depends on the domain layer. The domain layer has no external
  dependencies.
- **Explicit Rejection of Frameworks**: We favor custom implementations for critical security
  features, such as our own JWT handling with **Argon2** for password hashing, rather than relying
  on libraries like **Passport.js**.

## 3. Frontend Patterns

The frontend architecture is designed for performance and reusability, leveraging the "Islands
Architecture" pattern.

- **Astro for Static Content**: All pages and layouts are built with Astro to maximize static HTML
  rendering and minimize JavaScript.
- **React for Interactivity**: All dynamic and interactive components are built with React and
  hydrated on the client-side.
- **State Management**: Global state, particularly for authentication, is managed with **React
  Context**. A single `AuthProvider` wraps the entire application, providing a `useAuth` hook for
  components to consume.
- **Component Design**: We maintain a clear distinction between "smart" and "dumb" components.
  "Dumb" UI components are highly reusable and receive all their data via props, while "smart"
  components manage their own state or interact with the `AuthContext`.

## 4. Communication Patterns

- **API**: The frontend and backend communicate via a **RESTful API**.
- **Shared Types**: We use a dedicated `packages/types` workspace to share TypeScript types between
  the frontend and backend, ensuring type safety across the entire stack.
