# CSS Style Guide

We always use the latest stable version of TailwindCSS for all CSS. No configuration file is needed.
Only the `@tailwind` directive and some defaults are needed in the
`{project-name}/src/styles/global.css` file.

## CSS Class Formatting

Tailwind CSS classes in HTML and TSX should be written on a single line.

**Example:**

```html
<header
  class="flex items-center justify-between bg-sky-900 p-6 font-semibold text-sky-200"
></header>
```

## Custom Component Classes

We use the `@apply` directive to create custom, reusable component classes in our global stylesheet
(`global.css`). This helps to keep our markup clean and maintain a consistent design system.

**Example:**

```css
@layer components {
  .icon {
    @apply inline size-5;
  }

  .navLink {
    @apply flex flex-col items-center gap-2 hover:text-amber-200 lg:flex-row;
  }
}
```

## Default colors

We use the following default colors:

- `bg-zinc-800` for the main background color, NEVER USE full white background, prefer dark colors
- `text-zinc-200` for the main text color, NEVER USE full white text, prefer a shade of zinc
- `hover:text-sky-200` for the main hover text color, essentially for links

## Default font

We use the following default font:

- `font-sans` for the main font
