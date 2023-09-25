
## [React error handling with react-error-boundary](https://blog.logrocket.com/react-error-handling-with-react-error-boundary/#use-error-handler-hook)
[Yusuff Faruq](https://blog.logrocket.com/author/yusufffaruq/)
_This article was updated by_ [_Huzaima Khan_](https://blog.logrocket.com/author/huzaimakhan/) _on 24 May 2023_
## Using react-error-boundary
```
import { ErrorBoundary } from 'react-error-boundary'

function MyFallbackComponent({ error, resetErrorBoundary }) {
  return (
    <div role="alert">
      <p>Something went wrong:</p>
      <pre>{error.message}</pre>
      <button onClick={resetErrorBoundary}>Try again</button>
    </div>
  )
}

function MyComponent() {
  // Some component logic that may throw JS errors
}

function App() {
  return (
    <ErrorBoundary
      FallbackComponent={MyFallbackComponent}
      onReset={() => {
        // reset the state of your app here
      }}
      resetKeys={['someKey']}
    >
      <MyComponent />
    </ErrorBoundary>
  )
}
```

### Resetting error boundaries
```
import { ErrorBoundary } from 'react-error-boundary'

function ErrorFallback({ error, resetErrorBoundary }) {
  return (
    <div role="alert">
      <p>Something went wrong:</p>
      <pre>{error.message}</pre>
      <button onClick={resetErrorBoundary}>Try again</button>
    </div>
  )
}

function MyComponent({ someKey }) {
  // Some component logic that may throw JS errors
}

function App() {
  const [someKey, setSomeKey] = React.useState(null)

  return (
    <ErrorBoundary
      FallbackComponent={ErrorFallback}
      onReset={() => setSomeKey(null)} // reset the state of your app here
      resetKeys={[someKey]} // reset the error boundary when `someKey` changes
    >
      <MyComponent someKey={someKey} />
    </ErrorBoundary>
 
  )
}
```

### `useErrorHandler` Hook
```
import { useErrorHandler } from 'react-error-boundary'

function MyComponent() {
  const handleError = useErrorHandler()

  async function fetchData() {
    try {
      // fetch some data
    } catch (error) {
      handleError(error)
    }
  }

  return (
    ...
  );
}

function App() {
  return (
    <ErrorBoundary FallbackComponent={ErrorFallback}>
      <MyComponent />
    </ErrorBoundary>
  );
}
```

### `withErrorBoundary` function as HOC
```
import { withErrorBoundary } from 'react-error-boundary'

function MyComponent() {
  // Your component logic
}

const MyComponentWithErrorBoundary = withErrorBoundary(MyComponent, {
  FallbackComponent: ErrorFallback,
  onError: logErrorToService,
  onReset: handleReset,
  resetKeys: ['someKey']
});

function App() {
  return <MyComponentWithErrorBoundary someKey={someKey} />
}
```