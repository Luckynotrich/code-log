
```js

import { useContext, useEffect } from "react";
import Card from "./card";
import { useEventsQuery } from "../hooks/events-hook";
import EventContext from "../context/event-context";

export default function EventList() {
	const {Events, setEvents} = useContext(EventContext);
	const{data: events} = useEventsQuery();
	useEffect(()=> {
		setEvents(events)
	})
	return (
		<>
			{Events.map((event) => (
				<>
					<Card key={Event.event_id} Event={event} />
				</>
			))}
		</>
	);
};
```
