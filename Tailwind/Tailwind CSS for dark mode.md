To use Tailwind CSS for dark mode and apply styles based on focus, you need to enable dark mode in your Tailwind configuration and then use the `dark:` prefix for dark mode styles and `focus:` for focus styles.

1. Enable Dark Mode:

- **Configure Tailwind:** In your `tailwind.config.js` file, set `darkMode` to `media` or `class`.
    - `media`: Tailwind uses the browser's `prefers-color-scheme` media feature to determine dark mode based on the user's system preferences.
    - `class`: You'll need to manually add or remove the `dark` class to the root HTML element to toggle dark mode.
    ```js
    // tailwind.config.js
module.exports = {
  darkMode: 'media', // or 'class'
  // ...
};
```

2. Apply Styles:

- **Dark Mode:**
    Use the `dark:` prefix before any Tailwind CSS class to apply styles specifically in dark mode. 
    
- For example, `dark:bg-black` will set the background to black in dark mode. 

- **Focus:**
    Use the `focus:` prefix before any Tailwind CSS class to apply styles when an element is focused. 
    
- For example, `focus:outline-none` will remove the default outline on focus. 

Example:
```js
<button class="bg-blue-500 hover:bg-blue-700 text-white py-2 px-4 rounded focus:outline-none dark:bg-blue-700 dark:hover:bg-blue-500">
  Click Me
</button>
```

