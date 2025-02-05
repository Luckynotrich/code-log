
``` js

import React, { useState } from 'react';
const ImageDimensions = () => {
	const [dimensions, setDimensions] = useState({ height: 0, width: 0 });
	
	const handleImageLoad = (e) => {
			         const { naturalHeight, naturalWidth } = e.target;
				             setDimensions({ 
										height: naturalHeight,
									    width: naturalWidth 
							    });
		};
return (
		<div>
			<img 
				src={image_name}
				alt="example"
	            onLoad={handleImageLoad}
	            style={{ maxWidth: '100%' }}
             />
   <p>Image Height: {dimensions.height}px</p>
   <p>Image Width: {dimensions.width}px</p>
   </div>
 );
};
export default ImageDimensions;
```