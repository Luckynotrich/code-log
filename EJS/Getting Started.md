#### [Embedded JavaScript templating.](https://ejs.co/#install)


```bash
npm install ejs
```

```  Shell
touch ./view
touch ./view/index.ejs
```

basic usage
```js
const path = require("body-parser");

app.set("views", path.join(__dirname, "views"));
app.set('view engine', "ejs");
app.use(bodyParser.urlencoded({extended: false}))
```

To see how this is used see `/home/lucky/webdev/passport-tut-with-express-and-session_seekerslab/passport-js-tut/app.js` [`Comprehensive Passport.js youtube 22:45`](https://www.youtube.com/watch?v=7lsCSjZvZiI)


