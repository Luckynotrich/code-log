# See
```js
onClick={() => {
	logoutMutation.mutate();
	setTimeout(window.location.reload(),500);
	// history.go(-1);
	window.location.reload();
	// history.back(-1);
}}
```