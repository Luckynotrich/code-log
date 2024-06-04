# [Does ExpressJS support HTTP 2?](https://www.google.com/search?channel=fs&client=ubuntu-sn&q=does+node+express+support+http2)

### [ How to use HTTP2 with Express.js and test it locally. TypeOfNaN](https://typeofnan.dev/how-to-use-http2-with-express/)

Express.js is surprisingly lacking in HTTP/2 support. I have yet to find a resource that explains how to create an Express server with HTTP/2 support _and_ demonstrates how to set up a self-signed SSL cert for local testing. In this post, we’ll accomplish the following:

-   Create a minimal express server and observe it serving responses over HTTP/1.1
-   Use the `spdy` package to create a HTTP/2 server
-   Generate a self-signed SSL cert for local testing
-   Add some flexibility to run the app with or without https

## Create an Express app

Let’s first create an express app in a new directory. For simplicity’s sake, I’ll just accept all the npm defaults:

```bash
npm init -y npm install express touch index.js
```

Now let’s write a “Hello world” endpoint in our app:

```javascript
const express = require('express'); const PORT = 8000; const app = express(); app.get('/', (req, res) => { res.send('Hello world'); }); app.listen(PORT, () => { console.log(`App listening on port ${PORT}`); });
```

In our application’s directory, we can run `node .` and when we navigate to [http://localhost:8000](http://localhost:8000/) we will see “Hello world”. We can also pop open the network tab and note that this HTTP response was served using `http/1.1`.

[![http1](https://typeofnan.dev/static/401eff01b452217b77c75d4f0f1208b2/135f3/http1.jpg "http1")](https://typeofnan.dev/static/401eff01b452217b77c75d4f0f1208b2/135f3/http1.jpg)

## Adding spdy for HTTP/2

Express doesn’t have support for the native node `http2` module; however, the `spdy` package is a very popular alternative—at the time of writing this post, `spdy` is averaging 10 million weeky downloads.

Let’s install `spdy` and get our app working with `http2`!

Now we can make some updates to our `index.js` file. Note that this won’t be functional yet—we’ll still need to do some SSL configuration.

```javascript
const express = require('express'); const spdy = require('spdy'); const PORT = 8000; const app = express(); app.get('/', (_, res) => { res.send('hello world'); }); const server = spdy.createServer({}, app); server.listen(PORT, () => { console.log(`App listening on port ${PORT}`); console.log('SSL enabled'); });
```

Now let’s start our express app again:

It’s important to know that no modern browsers support HTTP/2 on _insecure connections_, so the `spdy` package will now be serving our app at **https**://localhost/8000. If we navigate to that URL, we should see an SSL warning that we can’t get around. Here’s what it looks like in Chrome:

[![No secure connection](https://typeofnan.dev/static/a3b8b18cd47576d2c9512507c9e90d0d/ea737/no-secure-connection.jpg "No secure connection")](https://typeofnan.dev/static/a3b8b18cd47576d2c9512507c9e90d0d/ea737/no-secure-connection.jpg)

Chrome is telling us that it doesn’t understand the protocol used by the SSL cert that our server is providing. That makes total sense because we’re not providing an SSL cert!

So how can we test this locally? We can generate a self-signed cert and pass that cert in the `spdy` configuration object.

## Creating a self-signed SSL certificate

To create a self-signed SSL cert, let’s first add some directories and scripts for repeatability—I’m making the assumption you’re on a development team and this process should be repeatable!

First, we’ll create a directory in which your cert and private key will live. We’ll also add an empty `.keep` file in that directory. The `.keep` file will make sure we check the directory in to Github despite having no other files in that directory.

```bash
mkdir cert touch cert/.keep
```

Next, we’ll create a `scripts` directory and a file for a script that will generate the cert.

```bash
mkdir scripts touch scripts/generate-cert.sh
```

Edit the new `generate-cert.sh` file and add the following code:

```bash
#!/bin/bash openssl req -nodes -new -x509 \ -keyout ./cert/server.key \ -out ./cert/server.cert \ -subj "/C=US/ST=State/L=City/O=company/OU=Com/CN=www.testserver.local"
```

This is a single command that will generate an SSL cert and associated private key. Since this is a self-signed cert for local use, the `subj` param doesn’t really matter and we can leave it as this generic value.

**Note:** This command assumes you have `openssl` installed on your machine, which is generally the case in unix (Mac/Linux) environments. If you’re on Windows, you may need to find another way to generate a self-signed cert!

Finally, edit `package.json` and add a command that will run the cert generation script:

```json
{ "scripts": { "generate-cert": "sh ./scripts/generate-cert.sh" } }
```

Assuming you are using git, you’ll want to make sure you git-ignore any generated certs/private keys. Create/edit a `.gitignore` file in the project’s root directory and make sure it has at least the following items:

```text
node_modules *.key *.cert
```

Now we have the ability to generate a self-signed cert and we made sure to ignore the generated files for git. Let’s give test it out:

If all goes according to plan, you now have a `server.cert` and `server.key` file in the `/cert` directory. Huzzah!

## Providing the cert and key to our server

Now that we have a cert and private key, we can provide them to our HTTP/2 server. We’ll do this by using the built-in `fs` module in `index.js`:

```javascript
const express = require('express'); const spdy = require('spdy'); const fs = require('fs'); const PORT = 8000; const CERT_DIR = `${__dirname}/cert`; const app = express(); app.get('/', (_, res) => { res.send('hello world'); }); const server = spdy.createServer( { key: fs.readFileSync(`${CERT_DIR}/server.key`), cert: fs.readFileSync(`${CERT_DIR}/server.cert`), }, app ); createServer(); server.listen(PORT, () => { console.log(`App listening on port ${PORT}`); console.log('SSL Enabled'); });
```

Let’s now start our server and see the self-signed cert in action:

If we go to **https**://localhost:8000 again, we see a new and exciting error message:

[![Invalid signing authority](https://typeofnan.dev/static/c7ee5de30c7ebd6491a4bf200584e177/1c72d/invalid-authority.jpg "Invalid signing authority")](https://typeofnan.dev/static/c7ee5de30c7ebd6491a4bf200584e177/6e52e/invalid-authority.jpg)

This is to be expected: your browser has no reason to trust the cert you generated locally. But this is fine: we know we generated it and it’s just for use during local development. In chrome, you can click “Proceed to localhost (unsafe)” to see the site running. Pop open the network tab and observe that the server is now using HTTP/2.

[![http2](https://typeofnan.dev/static/70e7084b28e748ccb999416b4a6a7a23/adce1/http2.jpg "http2")](https://typeofnan.dev/static/70e7084b28e748ccb999416b4a6a7a23/adce1/http2.jpg)

Congrats!

## Bonus: allow local development over http

You may or may not want to do local development with https. You can give yourself the option by creating an environment variable to opt out of https for local development. Let’s create an `SSL` environment variable and use that to opt in to using the HTTP/2 server:

```javascript
const express = require('express'); const spdy = require('spdy'); const fs = require('fs'); const PORT = 8000; const CERT_DIR = `${__dirname}/cert`; const useSSL = !!process.env.SSL; const app = express(); app.get('/', (_, res) => { res.send('hello world'); }); function createServer() { if (!useSSL) { return app; } return spdy.createServer( { key: fs.readFileSync(`${CERT_DIR}/server.key`), cert: fs.readFileSync(`${CERT_DIR}/server.cert`), }, app ); } const server = createServer(); server.listen(PORT, () => { console.log(`App listening on port ${PORT}`); console.log(`SSL ${useSSL ? 'enabled' : 'disabled'}`); });
```

Now, we can serve the app using SSL + HTTP/2 with an environment variable:

Or we can use the old express server by not providing the environment variable:

We have a lot of flexibility here: we can also just make this environment-dependent, have separate scripts in our `package.json` file, or use some other mechanism to decide which server to use.

## Conclusion

I was surprised to see the limited support for the native `http2` node module with Express. Fortunately, setting Express with HTTP/2 is not so bad with the help of the `spdy` package and self-signed certs.