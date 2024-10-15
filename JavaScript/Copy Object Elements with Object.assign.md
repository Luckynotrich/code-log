```js
let newEvent = {
	event_name: '',
	start_date: new Date(),
	end_date: new Date(),
	loc_id: 0,
	contact_id: 0,
	teaser: '',
	url: '',
	image: ''
}

  

let contactEvent = {contact_id: 1}

function ObjectAssign(){
	const activeEvent = Object.assign(newEvent,contactEvent)
	console.log(activeEvent)
}

ObjectAssign();
```