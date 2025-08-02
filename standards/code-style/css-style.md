# CSS Style Guide

We always use the latest version of TailwindCSS for all CSS.

## CSS Class Formatting

Tailwind CSS classes in HTML and JSX should be written on a single line.

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
