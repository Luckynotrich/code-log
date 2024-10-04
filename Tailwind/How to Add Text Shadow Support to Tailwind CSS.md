03/25/2022
[How to Add Text Shadow Support to Tailwind CSS](https://www.hyperui.dev/blog/text-shadow-with-tailwindcss)

If you prefer not to update the Tailwind CSS config, you can use JIT to write the following.

```
<h1 class="[text-shadow:_0_1px_0_rgb(0_0_0_/_40%)]">Hello</h1>
```

Alternatively, to use classes like `shadow-red-500`, you can do this.

```
<h1 class="[text-shadow:_0_1px_0_var(--tw-shadow-color)]">Hello</h1>
```