```js
import EventContext from "../context/event-context";
import { useContext, useEffect } from "react";
import Card from "./involve_card";
import { useEventsQuery } from "../hooks/events-hook";

export default function InvolveList() {
	const { data: events } = useEventsQuery();
	const { setEvents, involve, setInvolve } = useContext(EventContext); 
	const sortById = () => {
	setInvolve(
		events
			.toSorted((a, b) => b.event_id - a.event_id)
			.filter(
				(event) => event.event_name != "temp" && event.event_type === "inv"
			)
		);
	};

useEffect(() => {
	setEvents(events);
	sortById();
	}, [events, setEvents]);

  

return (

<>

{involve.map((event, i) => (

<div key={i}>

{event.event_name != "temp" && event.event_type === "inv" && (

<Card key={event.event_id} Event={event} />

)}

</div>

))}

</>

);

}
```