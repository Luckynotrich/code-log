[Geeks for Geeks](https://www.geeksforgeeks.org/how-to-embed-pdf-file-using-html/)
[W3 Schools](https://www.w3schools.com/tags/tag_object.asp)
- In addition to embedding a PDF file into a web page, the object tag can embed ActiveX, Flash, video, audio, and Java applets.
- Interactive documents can be attached to an object embedded with an HTML tag.
- It can be displayed according to your need on the screen by using the object’s height and width attributes.
```html
<!-- golf-call.html -->
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0">
	<title>Golf Call</title>
	<style>
	.pdf {
		width: 100%;
		height: 100%;
	}
	</style>
	</head>
<body>

<object data="./newledo_mini _golf_draft.pdf" width="800px" height="2100px" class="pdf">
</object>

</body>
</html>
```