
`/home/lucky/webdev/newledo/green-coast/src/utils/deleteEvents.js`
```js
import { getEvents, deleteEvent } from "../database/events.db.js";
import path from 'fs';
import { readdir, rm } from "node:fs/promises";

export async function deleteDatedEvents() {
	//readdir starts from root level
	const imageDir = './dist/images/';
	const files = await readdir(imageDir);

	let events = [];
	events = await getEvents(events);

	let today = new Date();
	//zero out time feature: hours,mins,secs
	today.setHours(0,0,0);

	await events.forEach((event) =>{
		let eventDate = event.start_date;
		eventDate.setHours(0,1,0);
		
		if(eventDate < today){
			if(files.some((file)=>file === event.image_name)){
				let deadFile = imageDir+event.image_name;
					rm(deadFile);
			}
			deleteEvent(event.event_id);
			console.log(event.event_name, " Deleted");
		}
		else console.log(event.event_name, 'Not deleted')

})

}
```