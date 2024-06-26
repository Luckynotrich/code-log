## [Get Started](https://quickref.me/ejs.html#get-started)

### Hello world

#### install

```
npm install ejs
```

#### hello.ejs

```html
<% if (user.email) { %>
  <h1><%= user.email %></h1>
<% } %>
```

#### CLI

```shell
$ ejs hello.ejs -o hello.html
```

### Render with Data

```
let ejs = require('ejs');

let people = ['geddy', 'neil', 'alex'];
let tpl = '<%= people.join(", "); %>';

let html = ejs.render(tpl, {people: people});
console.log(html);
```

Pass EJS a template string and some data.

### Browser Support

```
<script src="ejs.js"></script>
<script>
  let people = ['geddy', 'neil', 'alex'];
  let html = ejs.render('<%= people.join(", "); %>', {people: people});
</script>
```

Use ejs in a script tag.

### Variables

|   |   |
|---|---|
|`<%= var %>`|Prints the value of the variable|
|`<%- var %>`|Prints without HTML escaping|

### CLI

Render and specify an output file.

```shell
$ ejs hello.ejs -o hello.html
```

Feed it a template file and a data file

```shell
$ ejs hello.ejs -f data.json -o hello.html
```

### Comments

```html
<%# This line will denote a comment %>
```

---

```html
<%# This is a multi-line EJS comment.
    It can span multiple lines,
    but will not be displayed 
    in the final HTML output. 
%>
```

### Method

```
let ejs = require('ejs');
let template = ejs.compile(str, options);

template(data);
// => Rendered HTML string

ejs.render(str, data, options);
// => Rendered HTML string

ejs.renderFile(filename, data, options, function(err, str){
    // str => Rendered HTML string
});
```

### Including Files

```html
<%- include('partials/navbar.ejs') %>
```

Include a template with data:

```html
<% include('header', { title: 'My Page' }) %>
```

---

```html
<ul>
  <% users.forEach(function(user){ %>
    <%- include('item', {user: user}); %>
  <% }); %>
</ul>
```

To include a template, needs a file name option, paths are relative
## [Docs](https://quickref.me/ejs.html#docs)

### Conditionals

```html
<% if (userLoggedIn) { %>
  <p>Welcome, <%= username %>!</p>
<% } else { %>
  <p>Please log in.</p>
<% } %>
```

### Using loops

```html
<% if (userLoggedIn) { %>
  <p>Welcome, <%= username %>!</p>
<% } else { %>
  <p>Please log in.</p>
<% } %>
```

### Custom delimiters

```
let ejs = require('ejs'),
    users = ['geddy', 'neil', 'alex'];

// Just one template
ejs.render('<?= users.join(" | "); ?>',
    {users: users},
    {delimiter: '?'});
// => 'geddy | neil | alex'

// Or globally
ejs.delimiter = '$';
ejs.render('<$= users.join(" | "); $>',
    {users: users});
// => 'geddy | neil | alex'
```

### Caching

```
let ejs = require('ejs'),
LRU = require('lru-cache');

// LRU cache with 100-item limit
ejs.cache = LRU(100);
```

### Custom file loader

```
let ejs = require('ejs');
let myFileLoader = function (filePath) {
  return 'myFileLoader: ' + fs.readFileSync(filePath);
};

ejs.fileLoader = myFileLoader;
```

### Layouts

```
<%- include('header'); -%>
<h1>
  Title
</h1>
<p>
  My page
</p>
<%- include('footer'); -%>
```

## [#](https://quickref.me/ejs.html#client-side-support)Client-side support

### Example

```
<div id="output"></div>
<script src="ejs.min.js"></script>
<script>
  let people = ['geddy', 'neil', 'alex'],
      html = ejs.render('<%= people.join(", "); %>', {people: people});
  // With jQuery:
  $('#output').html(html);
  // Vanilla JS:
  document.getElementById('output').innerHTML = html;
</script>
```

### Caveats

```
let str = "Hello <%= include('file', {person: 'John'}); %>",
      fn = ejs.compile(str, {client: true});

fn(data, null, function(path, d){ // include callback
  // path -> 'file'
  // d -> {person: 'John'}
  // Put your code here
  // Return the contents of file as a string
}); // returns rendered string
```

## [](https://quickref.me/ejs.html#options)