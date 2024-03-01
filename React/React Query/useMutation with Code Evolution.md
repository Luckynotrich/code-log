
###  [Mutation](https://www.youtube.com/watch?v=NYCG1o38oEQ)
Start by creating state for input values using `useState`
![[Pasted image 20240104085948.png]]

Import `useMutation`
![[Pasted image 20240104084220.png]]

Next create a function call
![[Pasted image 20240104081348.png]]

Then create a function that uses axios to post the data
![[Pasted image 20240104081944.png]]

Import Use custom hook
![[Pasted image 20240104082818.png]]

import mutate
![[Pasted image 20240104083328.png]]

modify click function
![[Pasted image 20240104083509.png]]

Alias mutate
![[Pasted image 20240104083752.png]]

`isLoading, isError, error` are available for both `useMutation and useQuery` and would require aliasing to use simultaneously
![[Pasted image 20240104085043.png]]

### [Query Invalidation](https://www.youtube.com/watch?v=ldg3QIT53pI)
Causing query refresh as soon as server state is mutated
Using `useQueryClient` 
![[Pasted image 20240104102019.png]]

Then within the custom mutation hook implement the instance( in `useSuperHerosData.js`), adding an object with `onSuccess` that uses `queryClient` to invalidate `super-hero` query
![[Pasted image 20240104102933.png]]
f
### [set query data](https://www.youtube.com/watch?v=XI0SN5AI6YA)

![[Pasted image 20240103202829.png]]
In order to both post data to the server the author uses `queryClient.setqueryData` 
`'super-heroes'` is a query array. `oldQueryData.data` is the state of the array prior to the mutation . `data.data` refers to the hero object from the mutation response
![[Pasted image 20240103203710.png]]

### [Optimistic Updates](https://www.youtube.com/watch?v=rnN5ng6aoAc)

As the name implies update state before the mutation under the assumption that nothing can go wrong.

![[Pasted image 20240103204850.png]]
Defining the necessary functions: `onMutate` is called before the mutation is fired and receives the same variables the mutation receives. In this case the New Hero
![[Pasted image 20240103205239.png]]
