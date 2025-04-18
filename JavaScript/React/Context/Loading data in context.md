```js
import React, { createContext, useState, useEffect, useContext } from 'react';
```

// 1. Create the Context
```js
const DataContext = createContext(null);
```

// 2. Create a Provider
```js
function DataProvider({ children }) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);
```
  // 3. Fetch Data
  ```js
useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('your-api-endpoint');
        //This didn't work in developement
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const jsonData = await response.json();
        setData(jsonData);
      } catch (err) {
        setError(err);
      } finally {
        setLoading(false);
      }
    };

fetchData();
  }, []);
```

  // 4. Update Context
 ```js
return (
    <DataContext.Provider value={{ data, loading, error }}>
      {children}
    </DataContext.Provider>
  );
}
```

// 5. Consume Data
```js
function MyComponent() {
  const { data, loading, error } = useContext(DataContext);

if (loading) {
      return <p>Loading data...</p>;
    }
    if (error) {
      return <p>Error: {error.message}</p>;
    }

  return (
    <div>
      {/* Use the data */}
      {data && data.map(item => (
        <p key={item.id}>{item.name}</p>
      ))}
    </div>
  );
}

function App() {
  return (
    <DataProvider>
      <MyComponent />
    </DataProvider>
  );
}

export default App;
```