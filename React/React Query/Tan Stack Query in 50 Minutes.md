[Learn React Query In 50 Minutes](https://www.youtube.com/watch?v=r8Dg0KVnfMA)

```bash
npm i @tanstack/react-query
npm i @tanstack/react-query-devtools -D
```

```js
	import { QueryClient, QueryClientProvider,useQueryClient} from "@tanstack/react-query"
	
```
Wrap 
```js
const queryClient = new QueryClient(/* optionally default values here*/);

return (
<>
	<QueryClientProvider client={queryClient}>/* instantiates RQ functionality*/
		<App />
	<ReactQueryDevtools />
	</QueryClientProvider>
</>
```
![[`Pasted image 20231005092732.png`]]
The get posts function
![[Pasted image 20231005125529.png]]

### Query is just getting data from somewhere, a Mutation is changing some type of data
```js
import { useQuery, useMutation} from "@tanstack/react-query"
```
##### useQuery takes an object
queryFn: takes asynchronous function ===which must return a promise===
The video is using a function called wait to simulate network conditions
![[Pasted image 20231005094539.png]]
#### How queryKey works
Must be unique to query for instance:
![[Pasted image 20231005123144.png]]
The first query gets all the posts, the second gets a post by id, the third gets all the posts by author with id=1, and the fourth returns the "comments" of the post.id

![[Pasted image 20231005124029.png]]
queryKey: passing an object to the queryKey function allows the console.log outputs the data returned
![[Pasted image 20231005124422.png]]
##### If you need to see what is in the queryKey replace obj with {queryKey}

#### useQuery and by extension postQuery gives you access to a variety of state information
![[Pasted image 20231005125054.png]]


##### useMutation
![[Pasted image 20231005095839.png]]
![[Pasted image 20231005100209.png]]
### Devtools
![[Pasted image 20231005100554.png]]
### useQueryClient

![[Pasted image 20231005104202.png]]
![[Pasted image 20231005104412.png]]
## How all this works together with `useQuery`
![[Pasted image 20231005125845.png]]
Two different lists
![[Pasted image 20231005125952.png]]

List 1
![[Pasted image 20231005130143.png]]
![[Pasted image 20231005130041.png]]
List 2 is only different by the number in the h1 tag, but using the exact same query key just created on 2 separate pages. They are both initiating requests using the getPosts function show at the top of this file.
	
	The important thing is R.Q. will display cached data while simultaneously refreshing the data in the background and then react will update the page if the data has changed.
	
![[Pasted image 20231005135319.png]]

Any time you are fetching data `postQuery.fetchStatus` will equal `fetching`. If you are not fetching it will be in the `idle` status. If you are in the process of fetching data and loose internet connection  you will be in the `paused` state.

![[Pasted image 20231005140322.png]]

To understand how `useQuery.fetchStatus` and normal `useQuery.status` when your component first mounts `fetchStatus` will be fetching and `status` will be loading.

![[Pasted image 20231005141048.png]]
When the data comes back successfully 

![[Pasted image 20231005141234.png]]
If its an error `useQuery.status === "error"`

![[Pasted image 20231005141413.png]]
If you had data load successfully once, and you reload the page the above would be the current status.

![[Pasted image 20231005141721.png]]
The default behavior for when you are not fetching is the data goes 'stale'. 

![[Pasted image 20231005142150.png]]
It is possible to set `staleTime`. In this case the data will stay fresh for 5 minutes
![[Pasted image 20231005142418.png]]
Setting `staleIime` on individual queries can be achieved
![[Pasted image 20231005142648.png]]
Causing a `useQuery` to re-fetch at an interval

## New Sample code
![[Pasted image 20231005143113.png]]
Seemingly, Post searches based on id
![[Pasted image 20231005143646.png]]
The enabled code disables `userQuery` until after `postQuery` receives a `userId != null`
![[Pasted image 20231005143349.png]]

## Mutation Example 
The `App.jsx` body
![[Pasted image 20231005150220.png]]
The Create Post head code
![[Pasted image 20231005152217.png]]![[Pasted image 20231006090454.png]]
posts.js
![[Pasted image 20231006090604.png]]
#### `useMutation`
![[Pasted image 20231006090808.png]]

Optionally, variables can be passed, but function will be the same. Also,`useMutation` can accept properties including `onSuccess,onError, onMutate, onSetteles,`
![[Pasted image 20231006091827.png]]
Also,`useMutation` can accept properties including `onSuccess,``onError,` which would require an error rather than data.` onMutate,`  is called before mutation function and is where you would set context`  onSetteles,`
![[Pasted image 20231006101018.png]]
The only property for `useMutation` is a function for `mutationFn` ===which must return a promise===
![[Pasted image 20231006091918.png]]
Passing in an object with title and body


` onMutate,`  is called before mutation function and is where you would set context
![[Pasted image 20231006101549.png]]
Great for doing thing before the mutation takes place, or setting data inside context. 

If your mutation fails, `useMutation` doesn't retry like would happen with a query to make sure the action requested doesn't repeat multiple times while still failing the mutation.
		It is possible to say, add `retry 3` before the `onSuccess` and the `useMutation` will retry 3 times.

Any particular mutation will have many possible states including`error, idle,loading, success
![[Pasted image 20231006102730.png]]
The 'IS' property can be used to check `isError, isIdle, isLoading, isSuccess`