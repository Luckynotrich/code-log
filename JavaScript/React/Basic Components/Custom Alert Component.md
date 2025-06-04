For full control over the alert's appearance and behavior, create a custom component.
```js
import React, { useState } from 'react';

const Alert = ({ message, onClose }) => {
  return (
    <div className="alert-container">
      <div className="alert-content">
        <p>{message}</p>
        <button onClick={onClose}>Close</button>
      </div>
    </div>
  );
};

const MyComponent = () => {
  const [showAlert, setShowAlert] = useState(false);

  return (
    <div>
      <button onClick={() => setShowAlert(true)}>Show Alert</button>
      {showAlert && (
        <Alert message="This is a custom alert!" onClose={() => setShowAlert(false)} />
      )}
    </div>
  );
};
```