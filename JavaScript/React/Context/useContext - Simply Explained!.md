#### [Learn React Hooks: useContext - Simply Explained!](https://www.youtube.com/watch?v=HYKDUF8X3qI)

`context.jsx`
```js

import {createContext, useContext} from 'react';
import { User} from '../useContext';

export const DashboardContext = createContext(User);

export function useUserContext(){
	const user = useContext(DashboardContext);

	if (user=== undefined){
		throw new Error('useUserContext must be used with a DashboardContext');
	}
return user;
}
```

`index.jsx`
```js

import { useState } from 'react';
import { DashboardContext } from './context';

import Dashboard from './Dashboard';

export default function Demo({}){
const user = useState({
isSubscribed: true,
name: 'You',
});
return (
	<div>
		<DashboardContext.Provider value={user}>
			<Dashboar />
		</DashboardContext.Provider>
	</div>
)
}
```

`dashboard.jsx`
```js

import { Profile, Siderbar } from './Components';
import { User } from '.';

export default function Dashboard({user}){
	return (
	<div>
		<Sidebar />
		<Profile />
	</div>
	)
}
```

`components.jsx`
```js

//import { useContext} from 'react';
import {useUserContext} from './context';

export function SideBar({}){
	const user = useUserContext();
	
	return (
		<div>
			<div>user.name</div>	
			<div>Subscription Status: {user.isSubscribed}</div>	
		</div>
	)
}

export function Profile({}){
	const user = useUserContext();

	return <div>{user.name}</div>	
}
```