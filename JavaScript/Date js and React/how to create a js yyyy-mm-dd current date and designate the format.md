#### Here's how to create a current date string in "yyyy-mm-dd" format in JavaScript:

```js
function getCurrentDateFormatted() {
  const now = new Date();
  const year = now.getFullYear();
  const month = String(now.getMonth() + 1).padStart(2, '0'); // Month is 0-indexed
  const day = String(now.getDate()).padStart(2, '0');
  return `${year}-${month}-${day}`;
}

const currentDate = getCurrentDateFormatted();
console.log(currentDate);
```

#### To set a default value for a date input in React, the `defaultValue` attribute can be used on the `<input type="date" />` element. The value provided to `defaultValue` should be a string in the `YYYY-MM-DD` format.

```js
import React from 'react';

function DateInput({ defaultValue }) {
  return (
    <input type="date" defaultValue={defaultValue} />
  );
}

function App() {
  const today = new Date().toISOString().slice(0, 10); // Get today's date in YYYY-MM-DD format
  return (
    <div>
      <DateInput defaultValue={today} />
    </div>
  );
}

export default App;
```