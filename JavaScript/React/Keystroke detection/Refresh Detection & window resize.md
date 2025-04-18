[use-refresh-detection](use-refresh-detection.js)

### Both of these samples were intended to get the dimension of an image so that  a date could be positioned over the image. 
**The code below worked**
```js
//get the image dimensions on load/refresh
useEffect(() => {
if (refContainer.current) {
	const rect = refContainer.current.getBoundingClientRect();
	// console.log('rect.width ',parseInt(rect.width),'rect.height ',parseInt(rect.height))
	setDims({width: parseInt(rect.width), height: parseInt(rect.height)}); // Get the width and height
	}
}, [refContainer]); // Dependency array to re-run effect when ref changes
```

This approach didn't work, not sure why
```js
useEffect(() => {
	const handleBeforeUnload = () =>{
	console.log('handleBefore')
	sessionStorage.setItem('height',dims.height);
	sessionStorage.setItem('width',dims.width)
}

const handleReload = () => {
	console.log('handleReload')
	const height = sessionStorage.getItem("height") || 210;
	const width = sessionStorage.getItem("width") || 315;
	setDims({ width: parseInt(width), height: parseInt(height) });
}
window.addEventListener('beforeunload', handleBeforeUnload);
window.addEventListener('visibilitychange', handleReload); 
return () => {
	window.removeEventListener('beforeunload', handleBeforeUnload);
	window.removeEventListener('visibilitychange', handleReload);
	};
}, [dims]);
```

code Courtesy of `greenthecoast/frontend`
```js
import { useState, useEffect, useRef } from "react";
import PropTypes from "prop-types";
import DateBubble from "./date-bubble"; 

export default function ImageDate({
	image_name,
	moAbrev,
	startMo,
	endMo,
	startDa,
	endDa,
	}) {
	const refContainer = useRef();
	const [dims, setDims] = useState(); 
//get the image dimensions on load/refresh
useEffect(() => {
	if (refContainer.current) {
		const rect = refContainer.current.getBoundingClientRect();
		// console.log('rect.width ',parseInt(rect.width),'rect.height ',parseInt(rect.height))
		setDims({width: parseInt(rect.width), height: parseInt(rect.height)}); // Get the width and height
	}
}, [refContainer]); // Dependency array to re-run effect when ref changes 

	//get image dimensions when window is resized
	useEffect(() => {
		const handleResize = () => {
		setDims({
		width: refContainer.current.offsetWidth * 0.1,
		height: refContainer.current.offsetHeight * 0.99,
		});
	};
	window.addEventListener("resize", handleResize);
	return () => {
		window.removeEventListener("resize", handleResize);
	};
	}, []); 
return (
	<>
		<div className="relative z-0" ref={refContainer}>
		<img
			src={`${image_name}`}
			style={{ objectFit: "cover" }}
				className="mt-2 mr-1 pr-2 :mr-4 rounded-sm items-center z-20
				sm:w-[450px]
				md:ml-4"
			alt={image_name}
		/>
		</div>
		<pre style={{ height: `10px` }}>
			<DateBubble
				dims={dims}
				startDa={startDa}
				endDa={endDa}
				startMo={startMo}
				endMo={endMo}
				moAbrev={moAbrev}
		/>
		</pre>
	</>
	);
}

ImageDate.propTypes = {
	image_name: PropTypes.string,
	startDa: PropTypes.number,
	endDa: PropTypes.number,
	startMo: PropTypes.number,
	endMo: PropTypes.number,
	moAbrev: PropTypes.string,
};
```