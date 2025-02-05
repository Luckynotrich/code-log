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

Future Upon Review use with `react-hook-form`
`/home/lucky/webdev/future-upon-review/upon-review/src/components/category/data-list-input.jsx`

``` javascript
import React from 'react';

export default function DataListInput({ register, categories }) {
return (
	<>
	<label htmlFor="name">

<input
	autoComplete="off"
	{...register('name', {
	required: 'This is required',
	minLength: {
	value: 4,
	message: 'A minimum 4 characters is required.',
	},
	})}
	list="list-cats"
	id="name"
	name="name"
	type="text"
	autoFocus
	className="center"
	aria-describedby="create category name"
/>
</label>
<datalist id="list-cats" key={'list-cats'}>
	{categories.map(
		(cat) => (
		`${cat.name}`,
			(
			<option value={cat.name} key={cat.name}>
			{cat.name}
			</option>
			)
		)
	)}
	</datalist>
</>

);

}
```
