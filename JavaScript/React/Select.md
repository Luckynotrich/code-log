As one off
```ts
import { useForm, SubmitHandler } from "react-hook-form";
type inputs = {
event_type: string;
options: [string];
}
export default function App(){
const options = ["event", "ongoing"];
return(
	<select
            required
            maxLength={50}
            defaultValue="event"
            {...register("event_type")}
          >
          
            {options.map((value) => (
              <option key={value} value={value}>
                {value}
              </option>
            ))}
            
          </select>
        )
          }
```

As component
```js
import React from "react";
import ReactDOM from "react-dom";
import { Form, Input, Select } from "./components";

import "./styles.css";
export default function App() {
const onSubmit = (data) => console.log(data);

return (
<>
	<h1>Smart Form Component</h1>
	<Form onSubmit={onSubmit}>
		<Input name="firstName" />
		<Input name="lastName" />
		<Select name="sex" options={["female", "male"]} />
		<button>Submit</button>
	</Form>
</>
);
}
const rootElement = document.getElementById("root");
ReactDOM.render(<App />, rootElement);
```

```js
//components.jsx
import React from "react";
import { useForm } from "react-hook-form";

export function Form({ defaultValues, children, onSubmit }) {
  const { handleSubmit, register } = useForm({ defaultValues });

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      {Array.isArray(children)
        ? children.map((child) => {
            return child.props.name
              ? React.createElement(child.type, {
                  ...{
                    ...child.props,
                    register,
                    key: child.props.name
                  }
                })
              : child;
          })
        : children}
    </form>
  );
}

export function Input({ register, name, ...rest }) {
  return <input {...register(name)} {...rest} />;
}

export function Select({ register, options, name, ...rest }) {
  return (
    <select {...register(name)} {...rest}>
      {options.map((value) => (
        <option value={value}>{value}</option>
      ))}
    </select>
  );
}
```