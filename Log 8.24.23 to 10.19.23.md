### 8-24-2023 
I believe learning forms will be valuable. I don't know how valuable, but I think very.
I think learning react will be valuable. Same as above.

I learned about React [PropTypes](obsidian://open?vault=code-log&file=React%2FReact%20Prop-types). A way of implementing Variable Typing without a pre-processor.

### 8-25-2023
Leanne is coming to spend the weekend(Yay).
I got radio buttons to work with React-Hook-Form(RHF) yesterday. Today I have to add an [image](obsidian://open?vault=code-log&file=css%2FStyle%20Radio%20inputs) to represent the buttons.

Always check spelling and whether an import uses {} or default when an import is not found

### 8-28-2023
Installed Ubuntu Server 23.04 on [Media Server](obsidian://open?vault=code-log&file=Media%20Server) as well as kvm, libvirtd, 

### 9-7-2023
10 days Lapsed  minus 3 day weekend and one day feeling under the weather. Thought it was possible that I had COVID. Just Caffeine withdrawal.

Spent most of the time styling Future-Upon-Review
![[Pasted image 20230907150732.png]]
Just a note: This image was made in Gimp in which I have new experience 

Created ['How To use Font Awsome Icons in CSS'](obsidian://open?vault=code-log&file=css%2FHow%20to%20use%20Font%20Awesome%20Icons%20in%20CSS%20as%20background%20image) 
['A Checklist for choosing type-Fonts'](obsidian://open?vault=code-log&file=in%2FA%20checklist%20for%20choosing%20type%20%E2%80%93%20Fonts%20Knowledge%20-%20Google%20Fonts)
['Style Radio inputs'](obsidian://open?vault=code-log&file=css%2FStyle%20Radio%20inputs)

Yesterday and today: Spent time studying PASS
Created: [Read-Unread enhancement](obsidian://open?vault=code-log&file=PASS%2FRead-Unread%20enhancement)

### 9-7-2023
Star Rating color change working
Implemented Dark Light schemes(in FUR) using [Applying Dark Mode Styles in CSS by Ultimate Courses](https://ultimatecourses.com/blog/applying-dark-mode-styles-in-css)
Optional Technique by same: [Detecting Dark Mode in JavaScript](https://ultimatecourses.com/blog/detecting-dark-mode-in-javascript)

Made Pro/Con display optional(in Upon-Rreview) using: [LEARN REACT](https://react.dev/learn)/[Describing the UI](https://react.dev/learn/describing-the-ui)/ [Conditional Rendering](https://react.dev/learn/conditional-rendering)

### 9-11-2023
Completed Pro/Con optionality and added screen reset upon submit 

### 9-12-2023
Opened 'Git and GitHub' directory. Must master Git!
[Create GitHub Repo from the command line](obsidian://open?vault=code-log&file=Git%20and%20Github%2FCreate%20a%20GitHub%20repo%20from%20the%20command%20line)

### 9-13-2023
Added [Flex](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)to Large buttons in Future Self. 
Started a new webdev/[flex](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) directory for the tutorial linked here
Adding:: min-width: fit-content;
		and:: [overflow: scroll](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow); [CSS overflow Property](https://www.w3schools.com/cssref/pr_pos_overflow.php)
seemed to make the Large buttons and sections flex more consistently, but who knows. 
### I must keep notes AS I work,
not the following day as I am now.

### 9-14-2023
In an effort to handle refresh-redirect issues I ran 'npm run build' with the server pointed at
```javascript
res.sendFile(path.join(__dirname, '../','upon-review','dist','build','index.html')) 
```
Only got the html without any js.
By adding routes to the build assets(dist, snowpack) I was able to get the built version running.
### New Note Style
===Researching how to handle screen resets and redirecting=== on button down
capture resets Ctrl-r and F5(worked in upon-review/App.jss)
[KeyboardEvent Value (keyCodes, metaKey, etc)](https://css-tricks.com/snippets/javascript/javascript-keycodes/)
```javascript
const handleKeyDown = React.useCallback((e) => {
if((e.which || e.keyCode) == 116) {
e.preventDefault();/* disableKeyPressing(e); */
console.log('F5 is diabled now');
}

// Ctrl+R
if (e.ctrlKey && (e.which === 82) ) {
e.preventDefault();/* disableKeyPressing(e); */
console.log('Ctrl+R is pressed and refresh is diabled now');
}},[])

useEffect(() => {
window.addEventListener('keydown', handleKeyDown, true);
return () => {
window.removeEventListener('keydown', handleKeyDown, true);
};}, [handleKeyDown]);
```
[What Does $ Mean in JavaScript? Dollar Sign Operator in JS](https://www.freecodecamp.org/news/what-does-the-dollar-sign-mean-in-javascript/)

### 9-15-2023
### ===The above code was proved today===
[Detect Any KeyPress in React JS | Super Easy to Create KeyPress Based Applications](https://www.youtube.com/watch?v=D5SdvGMTEaU)
![[Pasted image 20230915085934.png]]
[How to add keyboard shortcuts to your React app](https://devtrium.com/posts/how-keyboard-shortcut)
![[Pasted image 20230915114900.png]]

### 9-18-2023
#### ===Experimenting with creating a router for review-form submit button.===
This worked like a link, but didn't complete writing to the DB
![[Pasted image 20230918092138.png]]
Link didn't work
![[Pasted image 20230918092638.png]]
Ditto
![[Pasted image 20230918092907.png]]

### 9-19-2023
#### Seems using a router is still left for build version
#### Started the process of allowing CatForm to edit categories yesterday
Complicated process:: converting preference text inputs to component. Still haven't gotten previously created category data to the components.
#### Turns out the final barrier is [React-Hook-Form] not allowing the value to be set.
[(using useFieldArray) example of what I am trying to accomplish](https://codesandbox.io/s/usefieldarray-conditional-2wi6f?file=/src/App.tsx)
I did manage to write to field array ,but printed field twice
```javascript
	
	useEffect(() => {
	const run = ()=> {
	append({ firstName: "bill", lastName: "luo" });
	setRan(true);
	}
	if() run();
	}, []); // you can use fields data in your useEffect
	
	
```
same:: tried to clear field array, but still printed twice
```javascript
	
	useEffect(() => {
	fields.map((item,index)=> remove(index))
	append({ firstName: "bill", lastName: "luo" });
	}, []); // you can use fields data in your useEffect
	
	
```
### 9-20-2023
#### [The winner! playground-react-vite/App_onClick_fieldArray.jsx](obsidian://open?vault=code-log&file=React-Hook-Form%2FForm%20Fields%20as%20an%20Array)
![[Pasted image 20230920095439.png]]
output
![[Pasted image 20230920092718.png]]
Requires the 'onClick' event which I can implement in the cat-name-form.jsx
The problem is:: can I alias 'fields' [YES](obsidian://open?vault=code-log&file=React-Hook-Form%2Fmultiple-useFieldArray)
```javascript
const {
fields: proFields,
append: proAppend,
remove: proRemove,
} = useFieldArray({
control,
name: "pros",
});
```
#### Installed React-hook-form-devtools
Check it Out!
### 9-27-2023
Seven FUCKING DAYS! This hasn't been a vacation, it's been a war between my brain and React-Hook-Form with GPT-Copilot throwing in a little confusion. 
[Adding boot partition to Grub](obsidian://open?vault=code-log&file=OS%20and%20Server%20setup%2FAdding%20boot%20partition%20to%20Grub)
[Mount USB - Community Help Wiki](obsidian://open?vault=code-log&file=OS%20and%20Server%20setup%2FMountUSB%20-%20Community%20Help%20Wiki)
[Form Fields as an Array](obsidian://open?vault=code-log&file=React-Hook-Form%2FForm%20Fields%20as%20an%20Array)
I went to Portland 9-20-2023 to attend CodePDX work session. Came back next day with silicone coating and started coating the carport roof. Finished by next day, so both Wednesday and Friday were 1/2 days. Two days lost to carport and then Saturday spent painting it. Sunday working on the MediaServer.
### 9-28-2023
Trying to understand why cat-form.jsx doesn't get data from create-cat-form.jsx. Its either the data isn't being communicated or react isn't waiting.

Finished converting cat-name-form to create-cat-form

 Started catObj.js in /utils
### 9-29-2023

Array.findIndex : : const categoryIndex = (id) => {categories.findIndex((cat) => cat.id === id)};

##### Obsidian is AWESOME! Just add the name of flavor of code ed: JavaScript after the first three back ticks and your code get highlighted.

catObject.js
```javascript
//takes in a cat object and returns a new cat object with the same properties
//or empty strings if the properties are undefined and id = 0 if id is undefined
export const catObj = (cat) => {
	let pros = [], cons = [], catName = '', id = null;
	if (cat.name !== undefined) catName = cat.name;
	if (cat.id !== undefined) id = cat.id;
	if (cat.pros !== undefined && cat.pros.length > 0 &&
		 cat.pros[0].value !== null) {
	pros = cat.pros.map((pro) => {
	return { value: pro.value, id: pro.id }
	})
	} else {
		 pros = ([...Array(5)].map((pro) => {
		return pro = {value: '', id: null} })) }
	if (cat.cons !== undefined && cat.cons.length > 0 &&
		 cat.cons[0].value !== null) {
	cons = cat.cons.map((con) => {
		return { value: con.value, id: con.id }
	})
	} else { cons = ([...Array(5)].map((con) => {
		return con = {value: '', id: null} })) 
		}
	return {
		name: catName,
		id: id,
		pros: pros,
		cons: cons,
	}
}
```

### 9-29-2023
Modified cat-form so it will allow user to edit Like/Dis-like values and append/delete fields for either in a category.  I finished the code above today. I also added 
```Javascript
const categoryIndexOf = (id) => {

// console.log('category-context::categoryIndexOf ', id.catId);

let index = categories.findIndex((cat) => cat.id === id);

return index;

};
```
These two allowed me to only pass the id of the category from create-cat-form to cat-form so it could use these functions to display the state of the category.

I also got Ubuntu desktop install completed on mediaserver.

### 10-2-2023
 ISSUE:: create-cat-form submit button does not display.
 Solution: set left position to a more reasonable setting.

Added Delete and Add icons to category-form

![[upon-delete-append.png]]

[Implemented https in ur-backend using](https://adamtheautomator.com/https-nodejs/)

###  10-3-2023
worked till 5:30 pm last night on Newledohub. That site is my relative position hell. If things work out here at Newledo perhaps I will implement flex box to reduce the heat :p

Back on the Newledohub trail today with Nicole's Windows box.


###  10-4-2023

I have [https](obsidian://open?vault=code-log&file=nodejs%2FNodejs%20https%20for%20development) running on ur-backend, but still can't get data to phone. I will continue to develop in http and think about a domain name.

I discovered [Tan Stack Query](obsidian://open?vault=code-log&file=Tan%20Stack%20Query%20in%2050%20Minutes)[(React Query)](obsidian://open?vault=code-log&file=React%20Query%2FReact%20Query(Tan%20Stack%20Query)) I created 2 different documents, but they are the same library. Now called Tan Stack Query and available for [ React Query, Solid Query, Svelte Query, Vue Query](https://tanstack.com/query)

###  10-5-2023
#### In creating the post above I discovered [SOLIDJS](https://www.solidjs.com/) which might be interesting to investigate
Today is the first day of working on the rest of the life of Show-Review. Time to get the whole thing working (the three main pages anyway)

### 10-10-2023
React-Router-Dom is a big bottle neck. Last week I started to investigate React Query and got some ways on a tutorial. Its complicated, today I decided to fix or destroy the router configuration I have in Upon Review `App.jsx`, but really got no where.
 
# Never try the react-router site tutorial again
 
Checkout VS Code Jupyter Notebook
### 10-11-2023
Today is the first day of working on the rest of the life of Show-Review. Time to get the whole thing working (the three main pages anyway)
Problem with Obsidian today can't seem to change to smaller font. 
But First I want to implement Tan Stack/React-Query

### 10-12-2023
 Last night modernized 'Detect-Refresh' code for detecting page refresh 

### 10-12-2023
The day of the Eclipser Mixer. 
Incorporating Detect-Refresh into react

### 10-19-23
I did work yesterday. I just didn't to this or to GitHub. We went to Astoria on Monday 10-16 after I spent some time working to understand `react-router-dom` better. I was/am trying to capture user resets. I interacted a bit 'Echo Pilot' $^T$$^m$ which gave me code that seems to capture the reset and prevent complete meltdown.
``` js
import { useState, useEffect } from 'react';
import { useNavigate } from 'react-router-dom';  

function UseRefreshDetection() {
const [refreshCount, setRefreshCount] = useState(0);
const navigate = useNavigate();  

useEffect(() => {
	const currentCount = sessionStorage.getItem('refreshCount') || 0;
	setRefreshCount(parseInt(currentCount));  

	const handleBeforeUnload = () => {
	sessionStorage.setItem('refreshCount', refreshCount + 1);
};  

	const handleRefresh = (event) => {
	event.preventDefault();
	 navigate('/');
};

	window.addEventListener('beforeunload', handleBeforeUnload);
	window.addEventListener('unload', handleRefresh);  

	return () => {
	window.removeEventListener('beforeunload', handleBeforeUnload);
	window.removeEventListener('unload', handleRefresh);
};
}, [refreshCount, navigate]);  

return refreshCount;
}

export default UseRefreshDetection;
```

#### Today 10-19-23
I am working with `useState` to cause `navigate` to work properly. I think it may refresh the current page only. 
	It turns out that using `useLocation` may be the solution. I was shown one [example](https://codesandbox.io/s/hardcore-tamas-vdyspf?file=/src/App.jsx) of how it could work.
	
````  js
import React /* , {useEffect, useCallback} */ from "react";
import { Routes, Route, Link, Outlet, useLocation } from "react-router-dom";
import Show2 from "./components/show-2.jsx"; //./components/categoryshow-2.js'
import Show3 from "./components/show-3.jsx"; //./components/review/review-category.jsx'
import Show1 from "./components/show-1.jsx"; //./components/reviewshow-1-review.jsx
import "./scss/App.scss";

function App() {
const [active, setActive] = React.useState([true, false, false]);
const handleClick = (index) => {
return () => {
	const newActive = [false, false, false];
	newActive[index] = true;
	setActive(newActive);
	};
};
let location = useLocation();
console.log(location);

return (
	<div className="App">
	<div className="routes">
	<Link to="/show-1">
		<button
			onClick={handleClick(0)}
			className={
				location.pathname === "/show-1" || location.pathname === "/"
				? "large-leftActive"
				: "large-left"
			}
			type="button"
			value="1"
			>						
			1
		</button>
	</Link>  

	<Link to="/show-2">
	<button
		onClick={handleClick(1)}
		className={
		location.pathname === "/show-2"
			? "large-centerActive"
			: "large-center"
			}
		value="2"
		type="button"
		>	
		2
	</button>
	</Link>
	<Link to="/show-3">
	<button
		onClick={handleClick(2)}
		className={
			location.pathname === "/show-3"
			? "large-rightActive"
			: "large-right"
			}
		value="3"
		type="button"
		>
		3
	</button>
	</Link>
	</div>
	<Outlet />

	<Routes>
		<Route exact path="/show-1" element={<Show1 />}></Route>
		<Route path="/show-2" element={<Show2 />}></Route>
		<Route path="/show-3" element={<Show3 />}></Route>
		<Route path="*" element={<Show1 />}></Route>
	</Routes>
	</div>

	);

}
```
