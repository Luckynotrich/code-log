# React-Query is good for managing arrays of data, but really fucks with you if all you want is the id from one form submit!

```sh
npm i @tanstack/react-query
npm i @tanstack/react-query-devtools -D
```

```js

	import { QueryClient, QueryClientProvider,useQueryClient} from "@tanstack/react-query"
	
```

`/webdev/newledo/green-coast/entry-form/src/components/hooks/contact-location-hook.jsx`
```js
  
import {useQuery} from '@tanstack/react-query';
import { getEvent } from "../../utils/entry-form-api";

const useContactLocatonQuery = (userId) => {

return useQuery({
	queryKey: ["event", userId],
	queryFn: () => getEvent(userId),
	staleTime: 1000 * 1 * 5, // 5 minutes
	cacheTime: 1000 * 60 * 60, // 1 hour
	refetchOnMount: true,
});
}
export const useEventQuery = (userId) => {

return useContactLocatonQuery(userId)
}
```

`/home/lucky/webdev/future-upon-review/upon-review/src/components/login_react.jsx`
```js

import { useMutation } from "@tanstack/react-query";
import axios from 'axios';
import UserContext from "./contexts/user-context";

export default function LogIn() {
const { setUserId, setUserEmail,setUserPassword } = useContext(UserContext);

const loginMutation = useMutation({
	mutationFn: async ({email,password}) => {
	await axios.post(`/users/login`+ password,email);
	},
	onSuccess: async (data) => {
	console.log('onSuccess =',await data)
	setUserId(await data);
	//setNotLoggedIn(false);
	},
	onSettled: ({email,password}) => {
	setUserEmail(email);
	setUserPassword(password);
},
onError: (error) => {
	return(<>error</>);
},
});
<form
	id='login'
	action='/users/login'
	method="post"
	target="_self"
	onSubmit={() => login.mutate}
>
...
...
...
```


