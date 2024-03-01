I set out to create multiple text input fields that referenced data in the db. This is the basic concept. 
``` js
import React from "react";
import { useForm, useWatch, useFieldArray } from "react-hook-form";
import "./styles.css";

export default function App() {
let arrayValues = [
{ name: "test", id: 123 },
{ name: "bill", id: 456 },
{ name: "test2", id: 789 }
];

const { control, handleSubmit, register } = useForm({
defaultValues: {
data: arrayValues,
},
mode: "onSubmit",
});

const { fields } = useFieldArray({
control,
name: "data",
});
return (
<form onSubmit={handleSubmit((data) => console.log(data))}>
{fields.map((data, index) => (
	<div key={arrayValue[index].id}>
	
	<input {...register(`data.${index}.name`)} />
	
	</div>
))}
  
<input type="submit" />
</form>
);
}
```
See the final code in the 
/webdev/playground-react-vite/App_multi_usefieldarray_rhf.jsx

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

