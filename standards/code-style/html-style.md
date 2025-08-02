# HTML Style Guide

## Structure Rules

- Use 2 spaces for indentation.
- Place nested elements on new lines with proper indentation.
- Content between tags should be on its own line when it is preceded or followed by other elements.

## Attribute Formatting

- Attributes should be placed on the same line as the opening tag.
- Use single quotes for attribute values, consistent with our Prettier configuration.

## Example HTML Structure

The following example is taken from the `NavBar.tsx` component and demonstrates our preferred style
for HTML and JSX.

```jsx
<header className='flex items-center justify-between bg-sky-900 p-6 font-semibold text-sky-200'>
  <nav className='mx-auto flex w-full max-w-screen-xl gap-4'>
    <ul className='flex w-full items-center justify-around'>
      <li>
        <a href='/' className='navLink'>
          <VscHome className='icon' aria-label='Home' />
          Home
        </a>
      </li>
      <li>
        <a href='/profile' className='navLink'>
          <VscAccount className='icon' aria-label='Profile' />
          Titux Metal
        </a>
      </li>
    </ul>
  </nav>
</header>
```
