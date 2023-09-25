This code seems like a winner though I don't really understand why it works and the prior one didn't: This code is in the playground
```
// App_use-field-array-conditional.jsx
import React from "react";

import {useForm, useWatch, useFieldArray} from "react-hook-form";
import "./styles.css";

const ConditionField = ({ control, index, register}) => {
const output = useWatch({
name: "data",
control
});

return (
<>
{/* Required shouldUnregister: false */}
{output[index]?.name === "bill" && (
<input {...register(`data.${index}.name`)} />
)}
{/* doesn't required shouldUnregister: false */}
<input
name={`data[${index}].easyConditional`}
style={{ display: output[index]?.name === "bill" ? "block" : "none" }}
/>
</>
);
};

export default function App(){
let arrayValues = [{ name: "test" }, { name: "test1" }, { name: "test2" }];
const { control, handleSubmit, register } = useForm({
defaultValues: {
	data: arrayValues
	},
	mode: "onSubmit"
});
const { fields } = useFieldArray({
control,
name: "data"
});

return (
	<form onSubmit={handleSubmit((data) => console.log(data))}>
	{fields.map((data, index) => (
	<>
		<input {...register(`data.${index}.name`)} />
			<ConditionField register={register} control={control} index={index} />
	</>
	))}

	<input type="submit" />

	</form>

	)

	};
```
This is code I delved into in my playground
```
	// App_onClick_fieldArray.jsx
	import React, {useEffect, useState} from "react";
	import { useForm, useFieldArray, Controller } from "react-hook-form";
	
	export default function App() {
	const { register, control, handleSubmit, reset, trigger, setError } = useForm({
	// defaultValues: {}; you can populate the fields by this attribute
	});
	
	const { fields, append, remove } = useFieldArray({
	control,
	name: "test"
	});
	
	const names =[['joe','Smith'],['jane','Doe'],['john','Doe']];
	
	return (
	
	<form onSubmit={handleSubmit(data => console.log(data))}>
	<ul>
	{fields.map((item, index) => (
	<li key={item.id}>
	<input {...register(`test.${index}.firstName`)} />
	<Controller
	render={({ field }) => <input {...field} />}
	name={`test.${index}.lastName`}
	control={control}
	/>
	<button type="button" onClick={() => remove(index)}>Delete</button>
	</li>
	))}
	</ul>
	
	<button
	type="button"
	onClick={() => {names.map((item,index)=> append({ firstName: item[0], lastName: item[1] }));}}
>	
	append
	</button>
	<input type="submit" />
	</form>
	
	);

}
```
[React Hook Form Tutorial - 14 - Arrays](https://www.youtube.com/watch?v=EbFW3u44xiY)
#### first create array
(shown in Type Script)
![[Pasted image 20230822081807.png]]

#### second add the property to default  values object
![[Pasted image 20230822082414.png]]

#### Create jsx
![[Pasted image 20230822084552.png]]

#### Run code and submit form
![[Pasted image 20230822084816.png]]

