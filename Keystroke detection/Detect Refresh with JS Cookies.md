
### [ Detecting Page Refreshes :: Using JavaScript on Client-Side](https://www.tedpavlic.com/post_detect_refresh_with_javascript.php)
``` js
<html>
<head>

**<script language="JavaScript"> <!--
function checkRefresh()
{
	//Ted's code uses var
	let cookieTime
	let cookieName
	// Get the time now and convert to UTC seconds
	let today = new Date();
	let now = today.getUTCSeconds();

	// Get the cookie
	let cookie = document.cookie;
	let cookieArray = cookie.split('; ');

	// Parse the cookies: get the stored time
	for(let loop=0; loop < cookieArray.length; loop++)
	{
		let nameValue = cookieArray[loop].split('=');
		// Get the cookie time stamp
		if( nameValue[0].toString() == 'SHTS' )
		{
			 cookieTime = parseInt( nameValue[1] );
		}
		// Get the cookie page
		else if( nameValue[0].toString() == 'SHTSP' )
		{
			 cookieName = nameValue[1];
		}
	}

	if( cookieName &&
		cookieTime &&
		cookieName == encodeURI(location.href) &&// was escape
		Math.abs(now - cookieTime) < 5 )
	{
		// Refresh detected

		// Insert code here representing what to do on
		// a refresh

		// If you would like to toggle so this refresh code
		// is executed on every OTHER refresh, then 
		// uncomment the following line
		// refresh_prepare = 0; 
	}	

	// You may want to add code in an _else_ here special 
	// for fresh page loads
}

function prepareForRefresh()
{
	if( refresh_prepare > 0 )
	{
		// Turn refresh detection on so that if this
		// page gets quickly loaded, we know it's a refresh
		let today = new Date();
		let now = today.getUTCSeconds();
		document.cookie = 'SHTS=' + now + ';';
		// Ted's code used escape() instead of encodeURI()'
		// document.cookie = 'SHTSP=' + escape(location.href) + ';';
		document.cookie = 'SHTSP=' + encodeURI(location.href) + ';';
	}
	else
	{
		// Refresh detection has been disabled
		document.cookie = 'SHTS=;';
		document.cookie = 'SHTSP=;';
	}
}

function disableRefreshDetection()
{
	// The next page will look like a refresh but it actually
	// won't be, so turn refresh detection off.
	refresh_prepare = 0;

	// Also return true so this can be placed in onSubmits
	// without fear of any problems.
	return true;
} 

// By default, turn refresh detection on
let refresh_prepare = 1;

-->
</script>**

</head>

<body **onLoad="JavaScript:checkRefresh();"** **onUnload="JavaScript:prepareForRefresh();"**>

<!-- The above is all that is needed. -->

<!-- Below is an example of the use of **disableRefreshDetection()** 
     to prevent false refreshes from being detected when forms 
     are submitted back to this page. If your web page does
     not use forms that post back to themselves, then the
     below does not matter to you. Omit it. -->

<!-- This is a dummy form. Focus on the **onSubmit**. -->

<form **onSubmit="JavaScript:disableRefreshDetection()"**>
<input type="submit" />
</form>

</body>
</html>
```