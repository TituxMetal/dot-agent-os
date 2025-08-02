# Linting Rules (ESLint)

Our project uses a shared ESLint configuration to enforce consistent code quality. The configuration
is split into a `base` set of rules and environment-specific overrides for `node` (backend) and
`web` (frontend).

## Base Configuration

The core of our linting strategy focuses on clean code, readability, and consistency.

- **Import Ordering**: Imports are strictly ordered and grouped to improve readability. The groups
  are: `builtin`, `external`, `internal`, `parent`, and `sibling`. Custom path aliases
  (`@auth-system/*` and `~/*`) are also configured.
- **Type-Only Imports**: We enforce the use of `import type` for all type-only imports to keep
  runtime code clean.
- **No Unused Variables**: All declared variables must be used. We allow unused function arguments
  or destructured variables that are prefixed with an underscore (`_`).
- **Arrow Functions**: We enforce a consistent style for arrow functions, requiring them to have an
  implicit return (`as-needed`) and parentheses around arguments (`as-needed`).

## Node.js (Backend) Configuration

The backend configuration extends the `base` rules and includes settings specific to our NestJS
environment.

- **Environment**: Configured for `node` and `jest`.
- **Key Overrides**:
  - `@typescript-eslint/no-explicit-any`: Disabled. While we strive for type safety, this is turned
    off to allow for flexibility where necessary.
  - `@typescript-eslint/explicit-function-return-type`: Disabled. We rely on TypeScript's type
    inference for function return types.

## Web (Frontend) Configuration

The frontend configuration is tailored for our Astro and React setup.

- **Plugins**: Includes `plugin:astro/recommended` and `plugin:astro/jsx-a11y-recommended` for
  Astro-specific rules and accessibility best practices.
- **Astro Files**: A specific parser and ruleset are applied to `.astro` files.
- **Test Files**: Test files (`.spec.ts`, `.test.ts`, etc.) are configured with the `vitest/globals`
  environment.
