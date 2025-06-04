To include a JavaScript component (or module) in an HTML file, you primarily use the `<script>` tag with the `src` attribute. This tag tells the browser where to find the JavaScript file to include. If you are using modules (using `import` and `export`), you can add `type="module"` to the `<script>` tag to enable the module features. 

Here's a breakdown of the process: 

1. [**1.** **Save the JavaScript component:**.](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=c28d7f4a7239b712&sxsrf=AE3TifN5Rur9TrRIqPecPI958_wzBtw1xw%3A1748452945995&q=Save+the+JavaScript+component&sa=X&ved=2ahUKEwj8uNTl1saNAxUgJTQIHSYhKJUQxccNegQIEhAD&mstk=AUtExfD9ITVNPqq--_fJkwlJur8A-3Cb87-DaxuNUJnUEBOyFgiwzATt6LVaYv2AuxtoprplpOtG3MGXLRf-vTI2NO3useACKmSRtsCJaTJDWjwIZgdp-X_eZ2k4EzGAvP3kvJo9pETbO0gmqaIsdUTxECrz2YLV-ER_GMd3ECdyh8I4xLFyiZ3tsMZgd8B6rrJtRl1ug5gvuzpnd9RMtA51sdt1TrIEbdHzy0UkXAFVpV5yxjawK6LZ5KuAaQZX-gFJSnrPZdWojMmUq3n2bk4DWXOw&csui=3)
    - First, create your JavaScript component and save it with a `.js` extension (e.g., `myComponent.js`).
    - [**2.** **Reference in HTML:**.](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=c28d7f4a7239b712&sxsrf=AE3TifN5Rur9TrRIqPecPI958_wzBtw1xw%3A1748452945995&q=Reference+in+HTML&sa=X&ved=2ahUKEwj8uNTl1saNAxUgJTQIHSYhKJUQxccNegQIFhAD&mstk=AUtExfD9ITVNPqq--_fJkwlJur8A-3Cb87-DaxuNUJnUEBOyFgiwzATt6LVaYv2AuxtoprplpOtG3MGXLRf-vTI2NO3useACKmSRtsCJaTJDWjwIZgdp-X_eZ2k4EzGAvP3kvJo9pETbO0gmqaIsdUTxECrz2YLV-ER_GMd3ECdyh8I4xLFyiZ3tsMZgd8B6rrJtRl1ug5gvuzpnd9RMtA51sdt1TrIEbdHzy0UkXAFVpV5yxjawK6LZ5KuAaQZX-gFJSnrPZdWojMmUq3n2bk4DWXOw&csui=3)   
Use the `<script>` tag in your HTML file, specifying the path to your JavaScript file using the `src` attribute. For example:
```js
   <script src="myComponent.js"></script>
```

[**1.** **Placement in HTML:**.](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=c28d7f4a7239b712&sxsrf=AE3TifN5Rur9TrRIqPecPI958_wzBtw1xw%3A1748452945995&q=Placement+in+HTML&sa=X&ved=2ahUKEwj8uNTl1saNAxUgJTQIHSYhKJUQxccNegQIKBAD&mstk=AUtExfD9ITVNPqq--_fJkwlJur8A-3Cb87-DaxuNUJnUEBOyFgiwzATt6LVaYv2AuxtoprplpOtG3MGXLRf-vTI2NO3useACKmSRtsCJaTJDWjwIZgdp-X_eZ2k4EzGAvP3kvJo9pETbO0gmqaIsdUTxECrz2YLV-ER_GMd3ECdyh8I4xLFyiZ3tsMZgd8B6rrJtRl1ug5gvuzpnd9RMtA51sdt1TrIEbdHzy0UkXAFVpV5yxjawK6LZ5KuAaQZX-gFJSnrPZdWojMmUq3n2bk4DWXOw&csui=3) 
You can place the `<script>` tag either within the `<head>` or `<body>` section of your HTML document. Placing it at the end of the `<body>` might improve page loading speed if the script is large and doesn't need to execute immediately. 

- [**2.** **Using Modules (if applicable):**.](https://www.google.com/search?client=ubuntu-sn&channel=fs&cs=1&sca_esv=c28d7f4a7239b712&sxsrf=AE3TifN5Rur9TrRIqPecPI958_wzBtw1xw%3A1748452945995&q=Using+Modules+%28if+applicable%29&sa=X&ved=2ahUKEwj8uNTl1saNAxUgJTQIHSYhKJUQxccNegQIKRAD&mstk=AUtExfD9ITVNPqq--_fJkwlJur8A-3Cb87-DaxuNUJnUEBOyFgiwzATt6LVaYv2AuxtoprplpOtG3MGXLRf-vTI2NO3useACKmSRtsCJaTJDWjwIZgdp-X_eZ2k4EzGAvP3kvJo9pETbO0gmqaIsdUTxECrz2YLV-ER_GMd3ECdyh8I4xLFyiZ3tsMZgd8B6rrJtRl1ug5gvuzpnd9RMtA51sdt1TrIEbdHzy0UkXAFVpV5yxjawK6LZ5KuAaQZX-gFJSnrPZdWojMmUq3n2bk4DWXOw&csui=3)
If your JavaScript component uses `import` and `export` statements, you'll need to add `type="module"` to the `<script>` tag. This tells the browser that the script is a module and should be treated accordingly.
```js
   <script type="module" src="myComponent.js"></script>
```

Example:
Let's say you have a JavaScript file named `myComponent.js` with some functions:
```js
// myComponent.js
export function greet(name) {
  console.log(`Hello, ${name}!`);
}
```

And you want to use it in your HTML:
```js
<!DOCTYPE html>
<html>
<head>
  <title>Importing JavaScript</title>
  <script type="module" src="myComponent.js"></script>
</head>
<body>
  <h1>My Page</h1>
  <script>
    // Assuming greet is exported from myComponent.js
    import { greet } from './myComponent.js'; 
    greet("World"); // This will print "Hello, World!" in the console
  </script>
</body>
</html>
```

Explanation:

- The `type="module"` attribute enables the `import` and `export` features within the `myComponent.js` file.
- The `import { greet } from './myComponent.js';` line imports the `greet` function from your JavaScript component.
- The `greet("World");` line then calls the imported function, printing a message to the browser's console.