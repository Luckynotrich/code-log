```js
export default function App() {
const { userId, defaultId } = useContext(UserContext);
const [isDisplayed,setIsDisplayed] = useState(false);
  
	useEffect(()=>
		{
		setInterval(()=>{
		setIsDisplayed(!isDisplayed)
		},3000);
		},[]
	);
return (
	<>
		{!isDisplayed && <Splash />}
		{ isDisplayed && <Main  />}
	</>)
}
```