 # [Tailwind Colors](https://tailwindcss.com/docs/customizing-colors)
Green the Coast `tailwind.config.js`
```js
/** @type {import('tailwindcss').Config} */
export default {
content: [
		'./index.html',
		'./public/**/*.html',
		"./src/**/*.jsx"
	],
	theme: {
	colors: {
		'green': '#02542D',
		'green-light': '#8CCE70',
		'tan-light': '#fefae0',
		'papaya-whip':'#faedcd',
		'border-color':'#383838',
		'dark-green': '#708947',
		'dark-gray':'gray-800',
		'dark-amber':'amber-600',
		'dark-yellow': 'yellow-700'
	},
	fontFamily:{
		sans:['Lato','sans-serif'],
		serif:['Pacifico','serif']
	},
	extend: {
	spacing: {
		'1': '8px',
		'2': '12px',
		'3': '16px',
		'4': '24px',
		'5': '32px',
		'6': '48px',
		}
	},
},

plugins: [],

}
```

 
 
 
 
 