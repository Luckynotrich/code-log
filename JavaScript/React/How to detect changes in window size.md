
To detect changes in window size in React, the `useEffect` hook and the `window.addEventListener` method can be utilized. This approach allows for the execution of side effects in functional components, specifically listening for the "resize" event on the window object. When the window is resized, a handler function is triggered, updating the component's state with the new dimensions.

```js
import React, { useState, useEffect } from 'react';

function WindowSizeDetector() {
  const [windowSize, setWindowSize] = useState({
    width: window.innerWidth,
    height: window.innerHeight,
  });

  useEffect(() => {
    const handleResize = () => {
      setWindowSize({
        width: window.innerWidth,
        height: window.innerHeight,
      });
    };

    window.addEventListener('resize', handleResize);

    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []);

  return (
    <div>
      <p>Window width: {windowSize.width}px</p>
      <p>Window height: {windowSize.height}px</p>
    </div>
  );
}

export default WindowSizeDetector;
```

In this example, `useState` initializes the `windowSize` with the current window dimensions. The `useEffect` hook then sets up an event listener for the "resize" event, calling `handleResize` whenever the window size changes. The `handleResize` function updates the `windowSize` state, causing the component to re-render with the new dimensions. The return statement within `useEffect` serves as a cleanup function, removing the event listener when the component `unmounts` or re-renders, preventing memory leaks.