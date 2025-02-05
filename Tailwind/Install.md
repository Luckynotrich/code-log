
```sh
npm install -D tailwindcss
npx tailwindcss init
```

# install tailwind with vite
```sh
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
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