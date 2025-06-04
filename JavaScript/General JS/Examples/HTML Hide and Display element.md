### Using JS
```html
<!DOCTYPE html>
<html>
<head>
    <title>Hide/Show Element</title>
	
	<!-- script type="module" required for import, but 
	functions must be attached to window.toggleHidden or loaded
	in basic <script></script> as below     -->
	<script type="module">
		import { Popup } from './pop-up.js';
	</script>
	
</head>
<body>

    <button onclick="{ toggleHidden('popup')}">Toggle Hidden</button>
    <<pop-up id="popup" onclick="{ toggleHidden('popup')}" hidden></pop-up>

    <script>
	function toggleHidden(elementId) {
		const element = document.getElementById(elementId);

		if (element.hasAttribute("hidden")) {
			element.removeAttribute("hidden");
		} else {
			element.setAttribute("hidden", "hidden");
		}
	}
    </script>

</body>
</html>
```

```js
export class Popup extends HTMLElement {
	constructor() {
	super();
	const shadow = this.attachShadow({ mode: 'open' });
	shadow.innerHTML = `
	<style>
	.Popup{
		background-color:rgb(116, 152, 190);
		color: black;
		border-radius: 5px;
		padding:.5rem;
		z-index: 10;
		}
	</style>
	<div class="Popup">
	<p>THIS IS A POPUP</p>
	</div>`
	}
}

customElements.define('pop-up', Popup)
```
### Using CSS
```html
<!DOCTYPE html>
<html>
<head>
    <title>Hide/Show Element</title>
    <style>
        .hidden {
            display: none;
        }
    </style>
</head>
<body>

    <button onclick="toggleVisibility()">Toggle Visibility</button>
    <div id="myDiv" class="hidden">
        This element can be hidden or shown
    </div>

    <script>
    function toggleVisibility() {
        var myDiv = document.getElementById("myDiv");
        if (myDiv.classList.contains("hidden")) {
            myDiv.classList.remove("hidden");
        } else {
            myDiv.classList.add("hidden");
        }
    }
    </script>

</body>
</html>

```