#### Today 10-20-23
Struggling with `react-router-dom` and Obsidian code formatting. On the latter, I was fighting phantom MD that mis-formatted my layout. I hope that the problem is O can't deal with large files, so I started a 'Log dating' naming convention.

`react-router-dom` is not very intuitive and offers a group of hooks that are not well exampled. It seems that most people/tutorials don't deal with many of the hooks. This [Log Rocket - Using Hooks with React Router](https://blog.logrocket.com/using-hooks-react-router/) is about the best I've found to date. 

`NavLink` is a component of R.R.D. [# React Router DOM: The Differences Between `NavLink`, Link, and `<a>`](https://javascript.plainenglish.io/react-router-dom-the-differences-between-navlink-link-and-a-bb5c27a48bfc)


```js
<Link to='/home'>Home</Link>

<Link
  to={{
    pathname: "/entrees",
    search: "?sort=rating",
    hash: "#the-hash",
    state: { showMenu: true }
  }}
/>
```

### Get Ubuntu setup with continuous updates

#### Today 10-23-23

#### [CSS Selector Reference](https://www.w3schools.com/cssref/css_selectors.php) This is a very handy link
[NavLink](https://reactrouter.com/en/main/components/nav-link#navlink)Also a very handy link

#### Today 10-25-23
Monday, I nailed down NavLink on [refresh-detected-react](~/webdev/refresh-detected-react). The key is in the CSS. React-Router adds an 'active' selector to which ever class is active, so to get styling other than just the default color change I used the following code.
NavLink simplifies the JS but complicates the CSS.
``` css
a[class*='large-'] {
	width: 99%;
	height: 90%;
	box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.4),
			0 6px 10px 0 rgba(240, 7, 7, 0.19);
	border-top-right-radius: 7px;
	border-top-left-radius: 7px;
	text-align: center;
	vertical-align: middle;
	padding: 1%;
	margin: 1% 0%;
}
.large-center {
	color: #cfad02;
	background-color: #FFDB00;
	left: 0.7%;
}
.large-left {
	color: #2e7d42;
	background-color: #0a6120;
	left: 0.7%;
}
.large-right {
	color: #94480a;
	background-color: #C46210;
	left: 0.7%;
}
a.active[class*='large-center'] {
	background-color: #FAFA37;
}
a.active[class*='large-left']{
	background-color: #8FD400;
}
a.active[class*='large-right']{
	background-color: #FF9933;
}
```

Tuesday, I converted Newledo happenings images to multiple size images for the web, edited the html to accept background images and started on a SCSS code generator to insert the images based on the screen size.(fun) 

Wednesday(today), I am continuing on the SCSS code generator.
### Links of the Day
[HTMLImageElement: naturalWidth property](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/naturalWidth)
[HTMLImageElement: naturalHeight property](https://developer.mozilla.org/en-US/docs/Web/API/HTMLImageElement/naturalHeight)
Above codes only work in the browser
``` html
<!DOCTYPE html>
<html>
  <head>
    <title>Title of the Document</title>
  </head>
  <body>
    <div>Click on img to see the result</div>
    <script>
      let img = document.createElement('img');
      img.id = 'imgId';
      img.src = '/uploads/media/default/0001/05/e9f3899d915c17845be51e839d5ba238f0404b07.png';
      document.body.appendChild(img);
      img.addEventListener("click", imgSize);
      function imgSize() {
        let myImg = document.querySelector("#imgId");
        let realWidth = myImg.naturalWidth;
        let realHeight = myImg.naturalHeight;
        alert("Original width=" + realWidth + ", " + "Original height=" + realHeight);
      }
    </script>
  </body>
</html>
```
The above code only works in the browser after the image loads

### Today 10.26.23
### Links of the day [image-size](https://www.npmjs.com/package/image-size)
``` bash
npm install image-size --save

```
Usage
```js
const sizeOf = require('image-size')

const dimensions = sizeOf('images/funny-cats.png')
console.log(dimensions.width, dimensions.height)

let width = sizeOf(file).width;
let height = sizeOf(file).height;

```