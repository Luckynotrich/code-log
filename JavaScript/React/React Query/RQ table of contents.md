### [Tan Stack Query in 50 Minutes](obsidian://open?vault=code-log&file=React%20Query%2FTan%20Stack%20Query%20in%2050%20Minutes)
is notes from a 'Web Dev Simplified by the same name'

###  [React Query(Tan Stack Query)](obsidian://open?vault=code-log&file=React%20Query%2FReact%20Query(Tan%20Stack%20Query))
is another 'Web Dev Simplified'

### [Devtools](https://tanstack.com/query/latest/docs/react/devtools)

```bash
npm i @tanstack/react-query
npm i @tanstack/react-query-devtools
```

```tsx
import { ReactQueryDevtools } from '@tanstack/react-query-devtools'
function App() {
	return (
	    <QueryClientProvider client={queryClient}>
	      {/* The rest of your application */}
	      <ReactQueryDevtools initialIsOpen={false} />
	    </QueryClientProvider>  
	    )
	}
```
### [Options](https://tanstack.com/query/latest/docs/react/devtools#options)

- `initialIsOpen: Boolean`
    - Set this `true` if you want the dev tools to default to being open
- `buttonPosition?: "top-left" | "top-right" | "bottom-left" | "bottom-right"`
    - Defaults to `bottom-left`
    - The position of the React Query logo to open and close the devtools panel
- `position?: "top" | "bottom" | "left" | "right"`
    - Defaults to `bottom`
    - The position of the React Query devtools panel
- `client?: QueryClient`,
    - Use this to use a custom QueryClient. Otherwise, the one from the nearest context will be used.
- `errorTypes?: { name: string; initializer: (query: Query) => TError}`
    - Use this to predefine some errors that can be triggered on your queries. Initializer will be called (with the specific query) when that error is toggled on from the UI. It must return an Error.
- `styleNonce?: string`
    - Use this to pass a nonce to the style tag that is added to the document head. This is useful if you are using a Content Security Policy (CSP) nonce to allow inline styles.

