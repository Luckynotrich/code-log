typeExample  given to demonstrate how useState could be used to store users 
**Not fully implemented**
![[Pasted image 20240709113901.png]]
Demonstrates **useCallback** to memoize
```js
import {useState, useEffect, useCallback} from 'react'
interface User{
  id: number,
  username: string,
}
function App() {                                         
   const [count, setCount] = useState<number>(0);
   const [users/* , setUsers */] = useState<User | null>(null);
   useEffect(()=>{
    console.log('mounting');
    console.log("Users: ", users);
    return ()=> console.log('unmounting');
   },[users])
                  //This is a memoized function( by useCallback I guess).
   const addTwo = useCallback(() =>setCount(prev => prev + 2),[])
  return (

    <>
     <div className='App'>
<h1>{count}</h1>
<button onClick={()=> setCount(prev => prev + 1)}>Add </button><br />
<button onClick={()=> addTwo()}>Add 2</button>
     </div>
    </>
  )
}

export default App;
```
![[Pasted image 20240709122221.png]]

```js
                 //the callback by itself dosent need type definition
   const addTwo = useCallback(() =>setCount(prev => prev + 2),[])
```

```js
		//'any' worked in vid, but not accepted by eslint 
const addTwo = useCallback((e: any): void =>setCount(prev => prev + 2),[])
```

```js
				// number worked
const addTwo = useCallback((e: number): void =>setCount(prev => prev + 2),[])
```

```js
import {useCallback,MouseEvent,KeyboardEvent} from 'react'
				//eslint & ts complained e never used
const addTwo = useCallback((e: MouseEvent<HTMLButtonElement> | KeyboardEvent<HTMLButtonElement>): void =>setCount(prev => prev + 2),[])
```

[MDN > Web APIs > KeyboardEvent > key](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key)

[Microsoft -typescript - `v3.7.7` ref: Interface KeyboardEvent](https://microsoft.github.io/PowerBI-JavaScript/interfaces/_node_modules_typedoc_node_modules_typescript_lib_lib_dom_d_.keyboardevent.html)

**Typescript 5.2.2**
```js

//final solution was to cheat
const addTwo = useCallback((e: MouseEvent<HTMLButtonElement> | KeyboardEvent<HTMLButtonElement>): void =>{setCount(prev => prev + 2),console.log(e)},[]);
```

