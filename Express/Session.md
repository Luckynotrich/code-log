

```
npm i express-session 
```

basic usage
```js
const express = require("express");
const { v4: uuidv4 } = require( 'uuid');
const session = require('express-session')
const FileStore = require("session-file-store")(session);

const app = express();
app.use(
	session({
		genid:(req)=> {
			console.log ("1. in genid req.sessionId: ",req.sessionId);
			return uuidv4();
		},
		store: new FileStore(),
		secret: 'a private key',
		resave: false,
		saveUninitialized: true // false will not create a sesson token
	})
);

app.get('/', (req,res)=> {

console.log("get / req.sessionId: ",req.sessionId);

res.send("<h1>get index route. /</h1>")

})

  

app.listen(3000, () => {

console.log("listening on port 3000");

})
```
how to capture session info. The -c' parameter causes curl to open a new session each time
```
curl -X GET http://localhost:3000 -c my-cookie.txt
```

The -b' parameter causes curl to reuse the session stored in `my-cookie.txt `each time while the session hasn't expired
```
curl -X GET http://localhost:3000 -b my-cookie.txt
```
