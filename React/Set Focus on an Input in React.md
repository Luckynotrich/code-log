## Make the user experience better by automatically applying focus to inputs


To set focus on an input in React:

1.  Set a reference on the input element
2.  Call the focus() method on the ref element

[

### Set focus on input on button click


```jsx
import {useRef} from ‘react’; 
function App() {
	const inputRef = useRef(null);
	return (
		 <div >
		 <input ref={inputRef}/>
		 <button onClick={() => {inputRef.current.focus()}}>Focus input</button> </div> 
				   ); }
export default App;
```

In the code above, you are creating a reference to the input field (inputRef), and upon pressing the button, you are referencing the inputRef and running the focus method on it.
[

### Set focus on input upon pressing enter


When the user clicks enter in one input, you may want to move them over into the next input. To do this, you need to create a method that runs each time a key is pressed by the user in an input. If the key code is that of the enter key, then you can change the focus to the next input.

```jsx
import {useRef} from ‘react’;
function App() {
const inputRef = useRef(null);
const inputRefTwo = useRef(null);
function checkPress(e){
	if(e.keyCode == 13){
	 inputRefTwo.current.focus();
	 } } 
	 return (
	  <div >
	   <input _ref_={inputRef} _onKeyPress_={(e) => checkPress(e)}/>
	   <input _ref_={inputRefTwo}/> </div> ); 
}
	    export default App;
```

### **Set focus on the input when the page is loaded**


Input can be focused when the page loads for a user by using the HTML autoFocus attribute, which is the most concise approach. Alternatively, a reference can be focused when the page is loaded using a useEffect hook, although that takes significantly more code to implements

```jsx
function App() { return ( <div> <input autoFocus /> </div> ); } export default App;
```

Hopefully, this tutorial helped you focus input automatically in React through various scenarios! Automatically applying focus to inputs can improve the user experience significantly by making it quicker for them to provide information to the application.
