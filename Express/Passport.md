[`PassportJS.org`](https://www.passportjs.org/)



```shell

npm install passport

```
or
```shell
npm i passport passport-local
```
The added installation of passport local allows the use of user names and passwords. It is also possible to login using services like Facebook and Google

`express-flash` is used by session to display messages like when the user fails to login
```
npm i express-session express-flash
```
`express-session` allows the user to persist across multiple pages 

basic usage
```js
const express = require("express");
const { v4: uuidv4 } = require( 'uuid');
const session = require('express-session');
const FileStore = require("session-file-store")(session);
const localStrategy = require("passport-local").Strategy;
const passport = require("passport");
  
const path = require('path');

const bodyParser = require("body-parser");

  

const app = express();

app.use(bodyParser.urlencoded({extended: false}));

  

const users = [{id: 1, email: "bob@bob.com"}];
  //requires views dir with login.ejs and success.ejs page
app.set("views", path.join(__dirname, "views"));
app.set('view engine', "ejs");

app.use(
	session({
		genid:(req)=> {
			console.log ("1. in genid req.sessionID: ",req.sessionID);
			return uuidv4();
		},
		store: new FileStore(),
		secret: 'a private key',
		resave: false,
		saveUninitialized: true // false will cause sesseion to only be saved when it is updated
	})
);
			// this localStrategy fails if username == fail
passport.use(// and succeeds on any other
	'login', // 'login' gives the use case a name that must have an authenticate route
	new localStrategy((username, password, done) => {
			// The done fucntion determines success/failure
		if(username =='fail'){
			// false as the 2nd param: User Input error. wrong pw, or email
			return done(null, false)
		}
		else{
			//if there is a user object as 2nd param: SUCCESS
			return done(null, { id: '123', email: username})
		}
	})
)

app.get('/', (req,res)=> {
	console.log("get / req.sessionID: ",req.sessionID);
	console.log("req.session.user:",req.session.user)
	req.session.user = users[0]
	console.log("req.sessionId: ",req.session);
	res.send("<h1>get index route. /</h1>")
})

app.get('/login', (req, res)=>{
	res.render("login")
}) 

app.get('/success', (req, res)=>{
	res.render("success")//case matches file name
})
  
app.get('/failed', (req, res)=>{
	res.send("failed")//message sent to screen
})

app.post("/login",function (req, res, next){
	console.log("Useless funciton")
	next();
	} ,//This is the default method for local strategy
passport.authenticate('login'/* was 'local' */,{
	session:false,
	failureRedirect: "FAILED",
	successRedirect:"/success"
}) //when using this strategy, no additional functions can be added.
)

app.listen(3000, () => {
	console.log("listening on port 3000");
})
```

[`Comprehensive Passport.js with Express & Sessions youtube 1hr`](https://www.youtube.com/watch?v=7lsCSjZvZiI)
For a more advanced Usage  see  `/home/lucky/webdev/passport-session-with-express_seekerslab/passport-js-tut/app.js`