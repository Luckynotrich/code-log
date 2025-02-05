```js

import {useSuspenseQuery} from '@tanstack/react-query';
import { getEvents } from "../utils/frontend-api";//src/utils/frontend-api.js
// eslint-disable-next-line react-refresh/only-export-components
const EventsQuery = () => {
	return useSuspenseQuery({
		queryKey: ["event/"],
		queryFn: () => getEvents(),
		staleTime: 1000 * 60 * 5, // 5 minutes
		cacheTime: 1000 * 60 * 60, // 1 hour
		refetchOnMount: true,
	});
}
export const useEventsQuery = () => {
	return EventsQuery()
	}
```

```js
import { Suspense } from "react";
import Header from "./header";
import Footer from "./footer";
import EventList from './event-list';
import Card from "./card";

export default function Events() {

return (
	<>
		<Header />
		<div
		className="bg-tan-light w-screen flex z-10 flex-col content-center
				xl:pl-[-1%] xxl:pl-[3%] 3xl:pl-[8%] 4xl:pl-[10.5%] 5xl:pl-[13%]"
				>			
					<div className="text-green flex-col flex-1 top-20 w-screen h-fit content-center">
						<h1 className="font-serif text-3xl ml-[4%] sm:mb-[2%] sm:ml-[20%]">
							Upcoming Events
						</h1>
				<Suspense fallback={<div><Card Event={defaultEvent} /><Card Event={alternate}/></div>}>
					<EventList />
				</Suspense>
				</div>
		</div>
	<Footer name="extern footer" />
	</>
);
}
```

```js

import Card from "./card";
import { useEventsQuery } from "../hooks/events-hook";
export default function EventList() {
const { data: events } = useEventsQuery();

return (
	<>
		{events.map((event, i) => (
			<>
				<Card Event={events[i]} />
			</>
		))}
	</>
);
}
```

####  Card.jsx : /webdev/newledo/green-coast/frontend/src/components/card.jsx
