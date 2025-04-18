```js
import { defineConfig } from 'vite'
export default defineConfig({
	root: './',
	server: {
		port: 5173,
		proxy:{
		"/":{
			target: "http/localhost:8080",
			changeOrigin:true,
			secure: false,
			ws: true,
		},
		"/images":{
			target: "http://localhost:8080",
			changeOrigin: true,
			secure: false,
			ws: false,
			rewrite: (path) => path.replace(/^\/images/, ''),
		},
		}
	}
})
```