[The Correct Way](https://github.com/react-hook-form/react-hook-form/issues/476)

### An Example
```
/* */import * as React from "react";
import PropTypes from "prop-types";
import { useController, useForm } from "react-hook-form";
import "./App.css";

const Checkboxes = ({ options, control, name }) => {
const { field } = useController({
control,
name,
});

const [value, setValue] = React.useState(field.value || []);

return (
<>
{options.map((option, index) => (
<label htmlFor={"controlled"}>
<input
onChange={(e) => {
const valueCopy = [...value];

// update checkbox value
valueCopy[index] = e.target.checked ? e.target.value : null;

// send data to react hook form
field.onChange(valueCopy);

// update local state
setValue(valueCopy);
}}

key={option}
type="checkbox"
value={option}
/>Number [{index+1}] {option}
</label>
))}
</>
);
};

Checkboxes.propTypes = {
options: PropTypes.array,
control: PropTypes.object.isRequired,
name: PropTypes.string.isRequired,
};

export default function App() {
const { register, handleSubmit, control } = useForm({
defaultValues: {
controlled: [],
uncontrolled: [],
},
});

const onSubmit = (data) => console.log(data);

// renderCount++;
let values = ["123", "456", "789"];
return (
<div>

<form onSubmit={handleSubmit(onSubmit)}>
<section>
<h2>uncontrolled</h2>
<label htmlFor={"uncontrolled"}>
<input {...register("uncontrolled")} type="checkbox" value={values[0]} />The first {values[0]}
</label>
<label htmlFor={"uncontrolled"}>
<input {...register("uncontrolled")} type="checkbox" value={values[1]} />The second {values[1]}
</label>
<label htmlFor={"uncontrolled"}>
<input {...register("uncontrolled")} type="checkbox" value={values[2]} />The third {values[2]}
</label>
</section>
<section>
<h2>controlled</h2>
<Checkboxes
options={["012", "345", "678"]}
control={control}
name="controlled"
/>
</section>
<input type="submit" />
</form>
</div>
);
}
```
