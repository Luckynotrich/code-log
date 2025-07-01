- `useHistory` hook (React Router v5 and earlier): If you are using an older version of React Router, you can use the `useHistory` hook.
```js
     import { useHistory } from 'react-router-dom';

     function MyComponent() {
       const history = useHistory();

       const handleClick = () => {
         history.push('/new-route'); // Navigate to '/new-route'
       };

       return (
         <button onClick={handleClick}>Go to New Route</button>
       );
     }
```

[net ninja](https://www.youtube.com/watch?v=TmVqwhBUiSM)
![[Pasted image 20240112101721.png]]

![[Pasted image 20240112101811.png]]
This will take you back one through history
![[Pasted image 20240112102646.png]]
This will take you to the root page
![[Pasted image 20240116071150.png]]