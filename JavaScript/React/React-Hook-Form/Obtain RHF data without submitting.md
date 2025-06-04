*To obtain form data in React Hook Form without submitting*, the `watch` or `getValues` methods can be used. The `watch` method allows subscribing to form values and triggers re-renders when the values change. The `getValues` method, on the other hand, retrieves the current form values without triggering re-renders or subscribing to changes.

```js
import React from 'react';
import { useForm } from 'react-hook-form';

function MyForm() {
  const { register, watch } = useForm();
  const name = watch("name");
  const email = watch("email");

  return (
    <form>
      <input {...register("name")} />
      <input {...register("email")} />
      <div>
        <p>Name: {name}</p>
        <p>Email: {email}</p>
      </div>
    </form>
  );
}
```

**Using `getValues`
```js
import React from 'react';
import { useForm } from 'react-hook-form';

function MyForm() {
  const { register, getValues } = useForm();

  const handleGetValue = () => {
    const data = getValues();
    console.log(data);
  };

  return (
    <form>
      <input {...register("name")} />
      <input {...register("email")} />
      <button type="button" onClick={handleGetValue}>
        Get Values
      </button>
    </form>
  );
}
```

**It's important to note that `getValues` retrieves form data at the moment it is called**, and it does not automatically update the UI. For real-time updates, `watch` is more suitable.