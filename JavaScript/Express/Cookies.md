# [ Understanding Cookies and Sessions in Node.js](https://dev.to/m__mdy__m/understanding-cookies-and-sessions-in-nodejs-3449)
## the structure of a cookie

[![Image description](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Ff7g2icuj4n5z6urrgm8y.png)](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Ff7g2icuj4n5z6urrgm8y.png)

1. **`name`**: The key or identifier for the cookie. It's the name by which the cookie is referenced.
2. **`value`**: The data stored within the cookie. This is the information the server wants to remember about the user.
3. **`expires`**: The date and time when the cookie will expire. After this, the cookie will automatically be removed.
4. **`path`**: This defines the scope of the cookie within the domain – which URLs the cookie should be sent to.
5. **`domain`**: Specifies which domain the cookie belongs to. It sets the scope of the cookie to the specified domain and its subdomains.
6. **`secure`**: A flag indicating that the cookie should only be sent over secure protocols like HTTPS.
7. **`HttpOnly`**: A flag that helps mitigate the risk of client side script accessing the protected cookie.
```js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  // "name" and "value"
  res.cookie('sessionId', '12345678', {
    // "expires" - The cookie expires in 24 hours
    expires: new Date(Date.now() + 86400000), 
    // "path" - The cookie is accessible for APIs under the '/api' route
    path: '/api', 
    // "domain" - The cookie belongs to the 'example.com' domain
    domain: 'example.com', 
    // "secure" - The cookie will be sent over HTTPS only
    secure: true, 
    // "HttpOnly" - The cookie cannot be accessed by client-side scripts
    httpOnly: true
  });

  // We can also use "maxAge" to specify expiration time in milliseconds
  res.cookie('preferences', 'dark_theme', {
    maxAge: 30 * 24 * 60 * 60 * 1000, // 30 days
    httpOnly: true // For security, also set "httpOnly" flag
  });

  res.send('Cookies are set with different attributes.');
});

const server = app.listen(3000, () => {
  console.log('Server running on port 3000...');
});

```