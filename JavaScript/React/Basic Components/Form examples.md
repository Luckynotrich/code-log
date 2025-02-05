```js
import React, { useState } from 'react';

function MyForm() {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
  });

  const handleChange = (event) => {
    setFormData({
      ...formData,
      [event.target.name]: event.target.value,
    });
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    // Do something with the form data, e.g. send it to an API
    console.log(formData);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        Name:
        <input 
          type="text" 
          name="name" 
          value={formData.name} 
          onChange={handleChange} 
        />
      </label>
      <label>
        Email:
        <input 
          type="email" 
          name="email" 
          value={formData.email} 
          onChange={handleChange} 
        />
      </label>
      <button type="submit">Submit</button>
    </form>
  );
}

export default MyForm;
```