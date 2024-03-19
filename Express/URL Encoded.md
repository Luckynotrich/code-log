``` js
app.use(express.urlencoded({extended: false}))
```

1. Setting this option to false ensures that  field names and data in the request are not encoded and thus accessible.