```jsx
import {
BrowserRouter as Router,
Routes,
Route,
Link
} from 'react-router-dom';

import Events from './components/events';
import Ongoing from "./components/ongoing";
import Home from './components/home';

export default function App() {
return (
	<div>
		<Router basename='/'>
			<Routes>
				<Route exact path='/' element={<Home />}/>
				<Route path='/events' element={<Events />}/>
				<Route path='ongoing' element={<Ongoing />}/>
			</Routes> 
		</Router>
	</div>
	);
}
function Header(){
const buttons =(
<Link to={'/'}><button>Home<button></Link>
)
}
```