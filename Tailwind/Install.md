
01  
### Install Tailwind CSS
Install `tailwindcss`, `@tailwindcss/postcss`, and `postcss` via npm.
```
npm install tailwindcss @tailwindcss/postcss postcss
```

02
#### Add Tailwind to your PostCSS configuration
Add `@tailwindcss/postcss` to your `postcss.config.mjs` file, or wherever PostCSS is configured in your project.
`postcss.config.mjs`
```
export default {  plugins: {    "@tailwindcss/postcss": {},  }}
```

03
#### Import Tailwind CSS
Add an `@import` to your CSS file that imports Tailwind CSS.
CSS
```
@import "tailwindcss";
```


```js
/** @type {import('tailwindcss').Config} */
export default {
	content: [
	 './pages/**/*.{html,js}',
    './components/**/*.{html,js}',
	],
	theme: {
	extend: {},
	},
plugins: [],

}
```