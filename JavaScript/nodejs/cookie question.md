I have a React, Express app that is running on a web-host using Express-sessions and Passport. The host is providing HTTPS/SSL service. The url exposes some ejs pages: a index page, signup and login. If I login with Chrome or Edge it works fine. 

If i login with Firefox I am returned to the index.  If I then add the direct path to the React app I can login using a react version of the login page.

Firefox warns that:  
 'Some cookies are misusing the recommended "SameSite" attribute' before I even login.  
After I try to login it warns:  
'Cookie "connect.sid" does not have a proper "SameSite" attribute value.'

This is what my Express Session code looks like
```js
app.use(expressSession({
	store: new pgSession({
	pool: pool,
	tableName: 'session'
// Insert connect-pg-simple options here
}),
	secret: process.env.SECRET,
	resave: false,
	saveUninitialized: false,
	cookie: {
		httpOnly: true,
		Secure: true,
		SameSite: "None",
		maxAge: 60 * 60 * 1000 * 5
}
// Insert connect-pg-simple options here
}))

app.use(passport.initialize());
app.use(passport.session());
```

Any ideas or recommendations? Questions?  
Thanks in advance. Rich