(Passport.js, Node, Express)
### References
[connect-pg-simple](https://www.npmjs.com/package/connect-pg-simple)   [MDN Web Docs, previously Mozilla Developer Network, HTTP headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)



passport local strategy
passport JWT strategy

Authentication vs Authorization: 
	Authentication is determining a persons identity.
	Authorization is determining a persons level of access.

Passport is a middle ware frame work for express that allows developers to create  other middle ware called strategies for identification and authorization.
		On each HTTP request, Passport will use a "Strategy " to determine whether the requester has permission to view that resource.
		If the user does not have permission, a 401 Unauthorized Error is thrown.
Passport Strategies?
	Each strategy uses the Passport JS framework as a template
	The Passport Local Strategy utilizes Cookies, Express Sessions, and some authentication logic.

Understanding http headers and cookies.
	Specifically http header called 'set cookie'  
		More specifically "Request and Response" headers
## [MDN HTTP headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers)
Request headers are basically meta data about our http request
	
	![[Pasted image 20240325093126.png]]
Response headers are a set of key/value pairs set by the server that include instructions created by the server for the requesting computer. 
	EX: set-cookie
	![[Pasted image 20240325094350.png]]

A cookie can be set as simply as creating a date in the browser console and using it to `setTime`.
Then writing it to the browser with `document.cookie`
![[Pasted image 20240325101205.png]]
We can see the cookie on the Application tab of Dev Tools in the Cookie folder
![[Pasted image 20240325101702.png]]
## Express Middleware

How exactly does Express middleware work?

```js
const express = require('espress');
const app = express();

app.get('/', (req,res) => {
res.send('<h1>Hello World</h1>')
})
app.listen(3000);
```

To better understand how this works you could write a function
```js
function stdExpressCallback(req,res,next){

}
```
or
```js
function stdExpressCallback(reqObj,resObj,nextMiddleWare){
	res.send('<h1>Hellow World</h1>');
}
```

Lets add a second function called middleware 1
```js
function middleware1(req,res,next){
console.log('I am a middleware');
next();
}
```

This looks like
```js
const express = require('espress');
const app = express();

function middleware1(req,res,next){
	console.log('I am a middleware');
	next();
}
function stdExpressCallback(reqObj,resObj,nextMiddleWare){
	resObj.send('<h1>Hellow World</h1>');
}

app.get('/',middleware1, stdExpressCallback)
app.listen(3000);
```

Express allows you to pass as many parameters to the different route functions as you want.

The example above is a route specific middleware. 

#### Global Middleware

```js
app.use(middleware1);
```

This looks like
```js
const express = require('espress');
const app = express();

app.use(middleware1);

function middleware1(req,res,next){
	console.log('I am a middleware');
	next();
}
function stdExpressCallback(reqObj,resObj,nextMiddleWare){
	console.log('I am a standard callback');
	resObj.send('<h1>Hellow World</h1>');
}

app.get('/', stdExpressCallback)
app.listen(3000);
```
##### [Order Matters]: 
in this case, because we declared `app.use(middleware1);` as a function that Express executes on every request it will appear in the console before the standard callback.

If we create other middleware functions, the order that they execute depends on where they appear in the app
```js
const express = require('espress');
const app = express();

app.use(middleware2);
app.use(middleware1);

function middleware1(req,res,next){
	console.log('I am middleware 1');
	next();
}
function middleware2(req,res,next){
	console.log('I am middleware 2');
	next();
}
function middleware3(req,res,next){
	console.log('I am middleware 3');
	next();
}
app.get('/', middleware3, (req,res,next) =>{
	console.log('I am a standard callback');
	res.send('<h1>Hellow World</h1>');
})
app.listen(3000);
```
The above console logs will appear in a 2, 1, 3 order with the standard route last.

##### Error handling in Express
```js
app.use(middleware);

function middleware (req, res, next){
	console.log('I am a middleware);
	
	const errOrb = new Error("I am an error");

	next (errObj);
	}
	
function errorHandler(err, req, res, next){
	if(err){
		res.send('<h1>There was an error, please try back later</h1>')}
}
```
The err parameter will contain information about the error and can be evaluated. 
Multiple error handling routes can be set to handle different errors.

This middleware function will catch all errors and print the message to the screen
```js
const express = require('espress');
const app = express();
app.use(middleware);

function middleware (req, res, next){
	console.log('I am a middleware);
	
	const errOrb = new Error("I am an error");

	next (errObj);
	}
	
function errorHandler(err, req, res, next){
	if(err){
		res.send('<h1>There was an error, please try back later</h1>')}
}



app.get('/', middleware3, (req,res,next) =>{
	console.log('I am a standard callback');
	resObj.send('<h1>Hellow World</h1>');
})
app.use(errorHandler);

app.listen(3000);
```
Note: the global `errorHandler` call just before the listener.
Express detects the error and bypasses the standard route and goes to the error handler.

###### It is possible to mutate/append to function parameters
```js
fconst express = require('espress');
const app = express();
app.use(middleware1);
app.use(middleware2);

function middleware1 (req, res, next){
req.customProperty = 100;
	next ();
	}
function middleware2 (req, res, next){
	console.log(`The custom property value is: ${req.customProperty}`);
	req.customProperty = 600;
	next ();
	}
	
function errorHandler(err, req, res, next){
	if(err){
		res.send('<h1>There was an error, please try back later</h1>')}
}
app.use(middleware1);
app.use(middleware2);


app.get('/', (req,res,next) =>{
	res.send(`<h1>The value is ${req.customProperty}</h1>`);
})

app.use(errorHandler);

app.listen(3000);
}
```
###### Based on the order of execution,
the above code will print 'The value is 600' because `app.use(middleware2)` comes after `app.use(middleware1)` 

## Intro to Sessions
[User Authentication in Web Apps - intro to session 1:05...](https://www.youtube.com/watch?v=F-sFp_AvHc8)
What is a session?
A session is a server side representation of state regarding the user that allow us to securely store  

([1:31:10](https://www.youtube.com/watch?v=F-sFp_AvHc8&t=5470s)) Implementation of Passport Local Strategy