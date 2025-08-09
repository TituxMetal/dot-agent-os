# Development Best Practices

## Context

Global development guidelines for Agent OS projects.

<conditional-block context-check="core-principles">
IF this Core Principles section already read in current context:
  SKIP: Re-reading this section
  NOTE: "Using Core Principles already in context"
ELSE:
  READ: The following principles

## Core Principles

### Keep It Simple

- Implement code in the fewest lines possible
- Avoid over-engineering solutions
- Choose straightforward approaches over clever ones

### Optimize for Readability

- Prioritize code clarity over micro-optimizations
- Write self-documenting code with clear variable names
- Add comments for "why" not "what"

### DRY (Don't Repeat Yourself)

- Extract repeated business logic to private methods
- Extract repeated UI markup to reusable components
- Create utility functions for common operations

### File Structure

- Keep files focused on a single responsibility
- Group related functionality together
- Use consistent naming conventions </conditional-block>

<conditional-block context-check="dependencies" task-condition="choosing-external-library">
IF current task involves choosing an external library:
  IF Dependencies section already read in current context:
    SKIP: Re-reading this section
    NOTE: "Using Dependencies guidelines already in context"
  ELSE:
    READ: The following guidelines
ELSE:
  SKIP: Dependencies section not relevant to current task

## Dependencies

### Choose Libraries Wisely

When adding third-party dependencies, ALWAYS ask the user to know if they have a preference for a
library in a particular context, NEVER make assumptions. If not, choose the most popular and
actively maintained option. Check the library's GitHub repository for:

- Recent commits (within last 6 months)
- Active issue resolution
- Number of stars/downloads
- Clear documentation </conditional-block>

---

## Git Workflow

We follow a strict, comprehensive Git workflow to ensure a clean, linear, and manageable codebase.

### 1. Branch Management

- **Never Commit to `main`**: All work must be done in a feature branch.
- **Create Feature Branches**: Always create a new branch from the latest `main`.
- **Branch Naming Convention**: Use a prefix and a short, descriptive name in kebab-case.
  - `feature/short-descriptive-name`
  - `fix/short-descriptive-name`
  - `docs/short-descriptive-name`
  - `chore/short-descriptive-name`
- **Link to Issues**: If the branch addresses a specific issue, include the issue number in the
  branch name (e.g., `feature/123-add-login-form`).

### 2. Commit Process

- **Conventional Commits**: All commit messages **must** follow the `type(scope): description`
  format. To enforce this, use `yarn commit` if available, or suggest the message title and the
  message description to the user in two separate blocks of Markdown formatted text.
  - **Types**: `feat`, `fix`, `docs`, `chore`, `refactor`, `style`, `test`.
  - **Description**: Start with a lowercase letter and keep it under 50 characters. Use present
    tense (e.g., "add" not "added").
  - **Breaking Changes**: Use `!` after the type/scope for breaking changes (e.g.,
    `feat(api)!: remove old endpoint`).
- **Atomic Commits**: Make small, incremental commits that represent a single logical change.

### 3. Pull Request (PR) Process

- **Create PRs for All Changes**: All code must be reviewed via a pull request before being merged
  into `main`.
- **Descriptive Titles**: PR titles should follow the same conventional commit format as commit
  messages.
- **Clear Descriptions**: The PR description should explain the "what" and "why" of the change.
  Reference any related issues using `fixes #123`.
- **Draft PRs**: Use draft pull requests for work that is still in progress but requires feedback.
- **Self-Review**: Always review your own code before marking a PR as ready for review.

### 4. Merging

- **Rebase Before Merging**: Before merging, rebase your feature branch onto the latest `main` to
  maintain a clean, linear history.
- **Merge Strategy**: Use a fast-forward merge whenever possible. For PRs, use the "Rebase and
  Merge" option.
- **Cleanup**: Delete the feature branch after it has been merged.

---

## Testing Strategy

A comprehensive testing strategy is essential for maintaining code quality and preventing
regressions. We employ different strategies for the backend and frontend to best suit their
respective architectures. We always collocate the test files with the code they test, in the same
level of the file structure. The test files are named like the code files, but with the suffix
`.spec.ts/tsx`. The only exception is for E2E tests, which are named like the code files, but with
the suffix `.e2e.ts/tsx`.

### Backend Testing (Jest)

Our backend testing is structured around the principles of **Clean Architecture**, with specific
types of tests for each layer.

- **Domain Layer**:
  - **Type**: Unit Tests
  - **Goal**: 100% coverage. Test all business logic, entities, and value objects in isolation.
  - **Tools**: Jest, with no external dependencies (no mocking of databases or services).
- **Application Layer**:
  - **Type**: Unit/Integration Tests
  - **Goal**: 90%+ coverage. Test the application services and use cases.
  - **Tools**: Jest, with mocked repository interfaces to isolate the application logic from the
    database.
- **Infrastructure Layer**:
  - **Type**: Integration/E2E Tests
  - **Goal**: 80%+ coverage. Test the controllers, database repositories, and other external-facing
    components.
  - **Tools**: Jest, with an in-memory SQLite database to test the full request/response lifecycle.

### Frontend Testing (Vitest & React Testing Library)

Our frontend testing focuses on component behavior and user interactions.

- **Unit Tests**:
  - **Scope**: "Dumb" UI components in isolation.
  - **Goal**: Verify that components render correctly based on their props.
  - **Tools**: Vitest, React Testing Library.
- **Integration Tests**:
  - **Scope**: "Smart" components and pages that involve multiple components and state management.
  - **Goal**: Test user flows, such as filling out a form or authenticating a user.
  - **Tools**: Vitest, React Testing Library, and a mocked API client to simulate backend responses.
