![[Pasted image 20240306134935.png]]

``` javascript
import React from "react";

export default function App() {
let brousers = ["Chrome", "Firefox", "Opera", "Microsoft Edge"];

return (
	<form action="submit">
		<label htmlFor="myBrowser">Choose a browser from this list:
		<input list="browsers" id="myBrowser" name="myBrowser" type="text"/>
		</label>
		//<<<--- Having text input inside of label probabley helped
		<datalist id="browsers">
			{brousers.map((bro) => (
				`${bro}`, //<<<---Don't ask me why, but this was the key
				<option value={bro} key={bro}>{bro}</option>
			))}
		</datalist>
		</form>

);

}
```