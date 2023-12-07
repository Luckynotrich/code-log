If you don't want to be annoyed by prop-types and 'no-unused-vars' error/warnings you can change .eslintrc.cjs rules thusly 

```js
rules: {
		'react-refresh/only-export-components': ['warn',
{ allowConstantExport: true },

],
	'react/prop-types': 'off',
	"no-unused-vars": "off"

},
```
