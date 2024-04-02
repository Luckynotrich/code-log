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
const path = require('path');

app.set("views", path.join(__dirname, "views"));
app.set('view engine', "ejs");

```

To see how this is used see `/home/lucky/webdev/passport-tut-with-express-and-session_seekerslab/passport-js-tut/app.js` [`Comprehensive Passport.js youtube 22:45`](https://www.youtube.com/watch?v=7lsCSjZvZiI)

####  **[Introduction to EJS](https://dev.to/victrexx2002/introduction-to-ejs-a-guide-to-building-dynamic-web-applications-2737)by [`Mgbemena Chinedu Victor`](https://dev.to/victrexx2002)
Examples of these extra tags are:

- **`<%`** and **`%>`**: These tags allow JavaScript code to run without outputting anything to the template. For example, you can use these tags to define variables or call functions.
- **`<%=`** and **`%>`**: These tags are used to output the result of a JavaScript expression to the template. For example, you can use these tags to insert data into the template.
- **`<%-`** and **`%>`**: These tags are used to output the result of a JavaScript expression to the template. However, unlike **`<%=`** and **`%>`** tags, they do not escape the output.
- **`<%#`** and **`%>`**: These tags add template comments.

Here's an example of what an EJS template looks like:

```js
<!DOCTYPE html>
<html>
<head>
  <title>My List</title>
</head>
<body>
  <% var message = "Hello, World!"; %>
  <h1><%= message %></h1>
  <%# This is a comment; it will not be included in the final output %>
  <% if (items.length === 0) { %>
    <p>No items to display.</p>
  <% } %>
</body>
</html>
```

## **Passing Data to EJS Templates**

EJS can pass data to templates and use that data to generate dynamic HTML. You can pass data to a template by providing an object as the second argument to the **`render`** function. For instance, let's say you want to pass a variable called **`name`** to your **`index.ejs`** template:  

```js
app.get('/', (req, res) => {
    res.render('index', { name: 'Alice' });
});
```

You can use the variable in your **`index.ejs`** template in this way:  

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>EJS FOR BEGINNERS</title>
</head>
<body>
    <h1>Hello <%= name %>!</h1>   
</body>
</html>
```

When the template is rendered, that is, when the script is executed, the **`name`** variable will be replaced with the value(**Alice**) passed to the **`render`** function.

## Using EJS to Include Reusable Template Components

EJS also allows you to combine different templates for different sections of your code, like your head, header, and footer sections.

You can add **`.ejs`** files to a current template using the **`<%- include (’file.ejs’) %>`** statement.

For example, if you have a template called **`header.ejs`** that you want to include in your **`index.ejs`** template, you can use the following code

in your **`index.ejs`** template:  

```js
// header.ejs
<header>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
    <h1>My Website</h1>
</header>
```

```js
// index.ejs
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>EJS FOR BEGINNERS</title>
</head>
<body>
        <header>
                    <%- include ('header.ejs') %>
        </header>
    <h1>Hello <%= name %>!</h1>   
</body>
</html>
```

This will include the contents of the **`header.ejs`** template to that point in the **`index.ejs`** template.

It is common practice to save templates that you will want to reuse across multiple pages in a **`partials`** sub-directory in the views directory.

To include the header in your code after doing this, attach the file path to the former syntax:  

```js
<%- include ('partials/header') %>
```

The `**<%- include %>**` tag makes it simple to reuse common HTML elements across multiple pages or views, simplifies code maintenance, and preserves a consistent look across your application.

