##### This example uses objects as data. The final implementation only used the string value. 
See /home/lucky/webdev/future-upon-review/upon-review/src/components/category/cat-mod-form.jsx
``` js
//~/webdev/playground-react-vite/srv/App_multi_usefieldarray_rhf.jsx
//Based on https://codesandbox.io/s/react-hook-form-multiple-usefieldarray-in-a-

form-ffboe?file=/src/index.js
import React from "react";
import { useForm, useFieldArray } from "react-hook-form";

import "./scss/App.scss";

export default function App() {
let cat = {
pros: [
	{ value: "test", id: 123 },
	{ value: "bill", id: 456 },
	{ value: "test2", id: 789 },
],

cons: [
	{ value: "strest", id: 234 },
	{ value: "brill", id: 567 },
	{ value: "strest too", id: 890 },
],
};

const { control, handleSubmit, register, watch } = useForm({
defaultValues: {
	pros: cat.pros,
	cons: cat.cons,
},
mode: "onSubmit",
});
  
const {
	fields: proFields,
	append: proAppend,
	remove: proRemove,
	} = useFieldArray({
	control,
	name: "pros",
});

const {
	fields: conFields,
	append: conAppend,
	remove: conRemove,
	} = useFieldArray({
	control,
	name: "cons",
});

return (

<form onSubmit={handleSubmit((data) => console.log(data))}>
	<ul>
	<fieldset>
		<legend>Pros</legend>
		{proFields.map((item, index) => {
return (
		<li key={item.id}>
		<input {...register(`pros.${index}.value`)} />
		<button
			type="buton"
			onClick={() => {
			proRemove(index);
			}}
			>
		Delete
		</button>
		</li>
	);
	})}
		<button
			type="button"
			onClick={() =>
			proAppend({ value: "" })}>
		Append
		</button>
	</fieldset>
	<fieldset>
		<legend>Cons</legend>
		{conFields.map((item, index) => {
			return (
				<li key={item.id}>
				<input {...register(`cons.${index}.value`)} />
				<button
					type="button"
					onClick={() => {
						conRemove(index);
					}}
				>
				Delete
				</button>
				</li>
				);
			})}
			<button
				type="button"
				onClick={() => conAppend({ value: "" })}
			>
			Append
			</button>
		</fieldset>
		</ul>
		<input type="submit" />
	</form>
	);
	}
```