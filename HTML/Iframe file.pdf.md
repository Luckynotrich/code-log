[Geeks for Geeks](https://www.geeksforgeeks.org/how-to-embed-pdf-file-using-html/)
[W3 schools](https://www.w3schools.com/tags/tag_iframe.asp)
- Using an iframe tag is the second way to embed a pdf file in an HTML web page. In web development, web developers use the iframe tag to embed files in various formats and even other websites within a web page.
- Due to its wide compatibility, the iframe tag is widely used for embedding pdf.
- A browser that does not support PDF documents or the object tag can also use this tag to embed a pdf HTML code.
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

<iframe src="./newledo_mini _golf_draft.pdf" width="800px" height="2100px" class="pdf">
</iframe>

</body>
</html>
```