# [Multer](https://expressjs.com/en/resources/middleware/multer.html)

```js
	const express = require('express')
	const app = express()
	const multer = require('multer')
	const storage = multer.diskStorage({
			destination: (req, file, cb) => {
				cb(null, 'ulploads/')
			},
		
			filename: (req, file, cb) => {
				cb(null, file.originalname)
			}
		})
	const upload = multer({storage})
	const port = 3000
	
	app.post('/api/upload', upload.single('file'), (req, res) => {
		res.send(req.file)
	})
	app.get('/', (req, res) => res.send('Hello World!'))
	app.listen(port, () => console.log(`Example app listening on port ${port}!`))
```


