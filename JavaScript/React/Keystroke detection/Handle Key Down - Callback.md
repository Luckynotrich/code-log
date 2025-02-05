```js
import React, {useEffect, useCallback} from 'react';
const handleKeyDown = useCallback((e) => {
	// F5
	if((e.which || e.keyCode) == 116) {
		e.preventDefault();
		location.reload();
		window.location.href = `${import.meta.env.PUBLIC_PROXY_URL}
}
	if (e.ctrlKey && (e.which === 82) ) {
		e.preventDefault();
		location.reload();
		window.location.href = `${import.meta.env.PUBLIC_PROXY_URL}
	}
},[])
useEffect(() => {
	window.addEventListener('keydown', handleKeyDown, true);
	return () => {
		window.removeEventListener('keydown', handleKeyDown, true);
};
}, [handleKeyDown]);
```