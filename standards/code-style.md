# Code Style

## 1. Formatting (Prettier)

Our code formatting is enforced by Prettier with the following configuration:

- **Arrow Parens**: `avoid`
- **Bracket Spacing**: `true`
- **JSX Single Quote**: `true`
- **Print Width**: `100`
- **Prose Wrap**: `always`
- **Semicolons**: `false`
- **Single Quote**: `true`
- **Tab Width**: `2`
- **Trailing Comma**: `none`

We also use the following Prettier plugins:

- `prettier-plugin-astro`
- `prettier-plugin-tailwindcss`

## 2. Linting (ESLint)

We enforce a strict set of linting rules using ESLint to maintain a high level of code quality and
consistency. For a detailed breakdown of our configuration, please see the
[Linting Rules](./code-style/linting-rules.md) guide.

## 3. Commit Messages

We use `commitizen` to ensure all commit messages follow the **Conventional Commits** specification.
This helps us to maintain a clear and descriptive git history.

## 4. Language-Specific Styles

For detailed style guides on specific languages, please see the following files:

- [CSS Style Guide](./code-style/css-style.md)
- [HTML Style Guide](./code-style/html-style.md)
- [TypeScript Style Guide](./code-style/typescript-style.md)
