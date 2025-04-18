# [Flash Messages for your Express](https://www.npmjs.com/package/express-flash)

Flash is an extension of `connect-flash` with the ability to define a flash message and render it without redirecting the request.

## Installation
Works with Express 3.x.x

```
npm install git://github.com/RGBboy/express-flash.git
```
## Usage

Set it up the same way you would `connect-flash`:
```js
  var flash = require('express-flash'),
      express = require('express'),
      app = express();
  app.use(express.cookieParser('keyboard cat'));
  app.use(express.session({ cookie: { maxAge: 60000 }}));
  app.use(flash());
```

Use `req.flash()` in your middleware
````js
app.get('/', function (req, res) {
    req.flash('info', 'Welcome');
    res.render('index', {
      title: 'Home'
    })
  });
  app.get('/addFlash', function (req, res) {
    req.flash('info', 'Flash Message Added');
    res.redirect('/');
  });
```