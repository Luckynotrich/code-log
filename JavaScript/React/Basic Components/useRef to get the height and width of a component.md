```js

import { useState, useEffect, useRef } from "react";
import PropTypes from "prop-types";

export default function Image({image_name, startMo, startDa}) {
	const refContainer = useRef();
	const [dims, setDims] = useState({
		width: 0,
		height:0,
	});

	useEffect(() => {
		setDims({
			width: refContainer.current.offsetWidth,
			height: refContainer.current.offsetHeight,	
		});
	}, []);
	//this statement covers gap betqween load and first refresh
	if(dims.height <= 0) setDims({width: 240,height:170})

return (
	<>
		<div className="relative z-0" ref={refContainer}>
		<img
		src={image_name}
		style={{ objectFit: "cover" }}
		className="mt-2 rounded-sm max-h-[170px] z-20"
		alt={image_name}
		/>
	</div>
	<pre>
	<div className="relative z-10" style={{ top: `-${dims.height}px` }}>
		<div className="flex flex-col items-center align-middle bg-tan-light w-10
			rounded-full leading-none text-sm">
			<div>{startMo}</div>
			<div>{startDa}</div>
		</div>
	</div>
	</pre>
	</>
	);
}
Image.propTypes ={
	image_name: PropTypes.string,
	startDa: PropTypes.number,
	startMo: PropTypes.string,
}
```
![[Pasted image 20241018121100.png]]

