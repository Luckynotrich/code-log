```js
useEffect(() => {
	let isMounted = true;
	const controller = new AbortController(); 

	const getUsers = async () => {
		try {
				const respose = await axios.get('/users', {
				signal: controller.signal
			});
			console.log(response.data);
			isMounted && setUsers(response.data)
		} catch (err) {
			console.error(err)
		}
	}
	getUsers();
	return () => {
	ismounted = false;
	controller.abort();
	}
}, [])
```