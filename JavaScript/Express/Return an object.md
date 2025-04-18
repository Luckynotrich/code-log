
#### In Express.js, an object can be returned as a JSON response using the `res.json()` method. This method automatically sets the `Content-Type` header to `application/json` and sends the object as a JSON string.
```js
app.get('/example', (req, res) => {
  const myObject = {
    message: 'Hello, world!',
    status: 'success',
    data: [1, 2, 3]
  };
  res.json(myObject);
});
```

#### Alternatively, `res.send()` can be used to send an object, but it requires manually setting the `Content-Type` header.

```js
app.get('/example2', (req, res) => {
  const myObject = {
    message: 'Hello, world!',
    status: 'success',
    data: [1, 2, 3]
  };
  res.set('Content-Type', 'application/json');
  res.send(JSON.stringify(myObject));
});
```

#### While both methods achieve the same result, `res.json()` is generally preferred for its conciseness and automatic header handling.
