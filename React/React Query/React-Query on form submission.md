### [awaited Promises](https://tkdodo.eu/blog/mastering-mutations-in-react-query#awaited-promises)

Promises returned from the mutation callbacks are awaited by React Query, and as it so happens, `invalidateQueries` returns a Promise. If you want your mutation to stay in `loading` state while your related queries update, you have to return the result of `invalidateQueries` from the callback:
``` js
{
  // 🎉 will wait for query invalidation to finish
  onSuccess: () => {
    return queryClient.invalidateQueries({
      queryKey: ['posts', id, 'comments'],
    })
  }
}
{
  // 🚀 fire and forget - will not wait
  onSuccess: () => {
    queryClient.invalidateQueries({
      queryKey: ['posts', id, 'comments']
    })
  }
}
```
### [Mutate or MutateAsync](https://tkdodo.eu/blog/mastering-mutations-in-react-query#mutate-or-mutateasync)
`useMutation` gives you two functions - `mutate` and `mutateAsync`. What's the difference, and when should you use which one?

`mutate` doesn't return anything, while `mutateAsync` returns a Promise containing the result of the mutation. So you might be tempted to use `mutateAsync` when you need access to the mutation response, but I would still argue that you should almost always use `mutate`.

You can still get access to the `data` or the `error` via the callbacks, and you don't have to worry about error handling: Since `mutateAsync` gives you control over the Promise, you also have to catch errors manually, or you might get an [unhandled promise rejection](https://stackoverflow.com/questions/40500490/what-is-an-unhandled-promise-rejection).
``` js
const onSubmit = () => {
  // ✅ accessing the response via onSuccess
  myMutation.mutate(someData, {
    onSuccess: (data) => history.push(data.url),
  })
}

const onSubmit = async () => {
  // 🚨 works, but is missing error handling
  const data = await myMutation.mutateAsync(someData)
  history.push(data.url)
}

const onSubmit = async () => {
  // 😕 this is okay, but look at the verbosity
  try {
    const data = await myMutation.mutateAsync(someData)
    history.push(data.url)
  } catch (error) {
    // do nothing
  }
}
```


[tkdodo on react query and forms](https://tkdodo.eu/blog/react-query-and-forms)

``` js
function PersonDetail({ id }) {
  const { data } = useQuery({
    queryKey: ['person', id],
    queryFn: () => fetchPerson(id),
  })
  const { register, handleSubmit } = useForm()
  const { mutate } = useMutation({
    mutationFn: (values) => updatePerson(values),
  })

  if (data) {
    return (
      <form onSubmit={handleSubmit(mutate)}>
        <div>
          <label htmlFor="firstName">First Name</label>
          <input
            {...register('firstName')}
            defaultValue={data.firstName}
          />
        </div>
        <div>
          <label htmlFor="lastName">Last Name</label>
          <input
            {...register('lastName')}
            defaultValue={data.lastName}
          />
        </div>
        <input type="submit" />
      </form>
    )
  }

  return 'loading...'
}
```