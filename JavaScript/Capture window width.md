``` javascript
const handleResize =() => {
	setW = (window.innerWidth)
	window.addEventListener("resize", handleResize);
	return()=> {
	window.removeEventListener("resize",handleResize);
	}
```

