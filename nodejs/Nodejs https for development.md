Turns out, the best way to see a development page that won't display on your phone is to implement https with a self issued key/cert pair, but you still have to copy the cert.pem to the trusted directory of your phone or browser. Anyway Firefox seems to not allow that anymore based on my research.
```bash
sudo apt list --installed | grep mkcert
sudo apt install mkcert

if(!project-name) mkdir project-name

cd project-name

if(!project-name init)  npm init -y

mkcert -key-file key.pem -cert-file cert.pem example.com *.example.com localhost
```

```bash
 mkcert -key-file key.pem -cert-file cert.pem example.com *.example.com localhost
Note: the local CA is not installed in the system trust store.
Note: the local CA is not installed in the Firefox and/or Chrome/Chromium trust store.
Run "mkcert -install" for certificates to be trusted automatically ⚠️

Created a new certificate valid for the following names 📜
 - "example.com"
 - "*.example.com"
 - "localhost"

Reminder: X.509 wildcards only go one level deep, so this won't match a.b.example.com ℹ️

The certificate is at "cert.pem" and the key at "key.pem" ✅

It will expire on 4 January 2026 🗓

```
test server

``` js
// Import builtin NodeJS modules to instantiate the service
const https = require("https");
const fs = require("fs");
  
// Import the express module
const express = require("express"); 

// Instantiate an Express application
const app = express();  

// Create an try point route for the Express app listening on port 4000.
// This code tells the service to listed to any request coming to the / route.
// Once the request is received, it will display a message "Hello from express server."
app.get('/', (req,res)=>{
res.send("Hello from express server.")
})

https.createServer(
// Provide the private and public key to the server by reading each
// file's content with the readFileSync() method.
{
key: fs.readFileSync("key.pem"),
cert: fs.readFileSync("cert.pem"),
},
app).listen(4000, () => {
console.log("serever is runing at port 4000");
});
//```

