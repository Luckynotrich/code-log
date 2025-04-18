Code form `image-date.jsx` in `greencoast`
```js
{
let moAbrev ='Feb,
startMo = 2,
endMo = 3,
startDa=28,
endDa = 3,
let wide, ex = startDa/10 + endDa/10, EX = false
if (endDa > startDa || endMo > startMo) wide = true;
else wide = false;
if(ex > 4)EX = true;
return (
	<div className={`flex flex-col items-center align-middle
		bg-tan-light h-12 p-[8px] border-[1px]
		rounded-full leading-4 text-md ${EX ? "w-20" :wide ? "w-16" : "w-12"}`}>
			<div>{String(moAbrev)}</div>
			<div className="flex flex-row">
			<div>{String(startDa)}</div>
			{wide && <div>-{endDa}</div>}
		</div>
	</div>
)}
```