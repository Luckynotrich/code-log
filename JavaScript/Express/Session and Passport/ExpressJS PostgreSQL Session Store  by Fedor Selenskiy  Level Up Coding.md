## Background

**Session** is data about a user, which is stored on the server.

**Cookie** contains the session ID, and it is stored on the client side.

Cookies and sessions are great for improving user experience — user data can be stored on the server that keeps track of what the user has done, so they don’t have to do it again. This is great when the user starts filling out a form, but has to come back to it later. When they do, they’re happy to see that their progress hasn’t been lost.

## Setting Up the Database

First, I created a database called `express-store-test` (the name of the database doesn’t really matter).

Then I added a table called `session` — express will automatically look for this table for finding the session data. This table should have 3 columns, which are:

![](https://miro.medium.com/v2/resize:fit:875/1*eKnZk-rTfGJbdcHvyJ8PVg.png)

-   `sid` is the session id — this is the what cookies reference.
-   `sess` contains the session as a JSON object
-   `expire` contains the expiration timestamp for the current session

## Adding Express Middleware

I used [connect-pg-simple](https://www.npmjs.com/package/connect-pg-simple) middleware. I added it to the project with:

`npm i express-session connect-pg-simple`

```js
import express from 'express';  
import session from 'express-session';  
import genFunc from 'connect-pg-simple';  
  
const PostgresqlStore = genFunc(session);  
const sessionStore = new PostgresqlStore({  
  conString: '<insert-connection-string-here>',  
});  
  
const app = express();  
app.use(express.json());  
  
app.use(session({  
  secret: 'secret',  
  resave: false,  
  saveUninitialized: false,  
  cookie: cookieOptions, // define cookieOptions  
  store: sessionStore  
}));
```

See [session options](https://expressjs.com/en/resources/middleware/session.html#options) and [cookie options](https://expressjs.com/en/resources/middleware/cookie-session.html#cookie-options).

The PostgreSQL connection string has the following format:

`postgres://<user>:<password>@<address>:<port>/<database-name>`

If you are using pgAdmin, you can view the address and port by right clicking the PostgreSQL server in the browser panel and clicking `properties`. Under the `connection` tab, you can view the address and port:

![](https://miro.medium.com/v2/resize:fit:658/1*Sn99WiM6A-fFmA_k6rmDzw.png)

Right click PostgreSQL server -> Properties -> Connection

## Accessing the Session

You can access the session object inside a request handler:

```
app.get('/whoami', (req, res, next) => {  
  const name = req.session.name  
  res.send('Your name is: ', name);  
});
```

You can set session data just as you would normally with a JSON object:

```
app.post('/update/name', (req, res, next) => {  
  req.session.name = req.body;  
  res.send('Your name is now: ', req.session.name);  
});
```

## Conclusion

I described a way to setup a PostgreSQL database to store express session data. Express is fantastic because it abstracts away from the session store, replacing the PostgreSQL store with any other supported store would require you only to change the value of the `sessionStore` variable.