
# [Set-Cookie](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie#samesitesamesite-value)
## the structure of a cookie


1. **`name`**: The key or identifier for the cookie. It's the name by which the cookie is referenced.
2. **`value`**: The data stored within the cookie. This is the information the server wants to remember about the user.
3. **`expires`**: The date and time when the cookie will expire. After this, the cookie will automatically be removed.
4. **`path`**: This defines the scope of the cookie within the domain – which URLs the cookie should be sent to.
5. **`domain`**: Specifies which domain the cookie belongs to. It sets the scope of the cookie to the specified domain and its subdomains.
6. **`secure`**: A flag indicating that the cookie should only be sent over secure protocols like HTTPS.
7. **`HttpOnly`**: A flag that helps mitigate the risk of client side script accessing the protected cookie.