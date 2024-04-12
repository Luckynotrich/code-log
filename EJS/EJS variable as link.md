Image as value for a link
```html
<a href="./dist/css/happenings/minigolf01.png" target="_self">
	<img src="./images/upcoming/minigolf01.png" alt="Mini Golf Promo" />
</a>
```

Call to EJS file
```js
// only using the absolute path as the route worked
app.get('/dist/css/happenings/:id',(req,res,next) =>{
	let id = req.params.id;
	console.log('id =',id)
	res.render('index.ejs', {file: `/images/upcoming/${id}`});
next();
})

//the get above along with the root path below was the only solution that worked
app.use(express.static(path.join(__dirname,'./')));
```

Not completely clear on what was going on. Too many variables with html handing off to Express which has to hand off to ejs which then has to get the image file from Express which has to use the correct path to find the image. 

EJS 
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<link rel="stylesheet" href="image-display.css">
	<title>NewLedo Image</title>
	<link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
	<img src="<%=file%>" alt="Oops! Couldn't find <%=file%> ">
</body>
</html>
```