[NavLink](https://reactrouter.com/en/main/components/nav-link#navlink)
``` js
function App() {
const [isDefault, setisDefault] = useState(false);
useEffect(() => {
	if (!isDefault) {
		setisDefault(true);
	}
}, []);
return (
<div className="App">
	<div className="routes">
	<NavLink
		to="/"
		id="large-left"
		className={({ isActive, isPending, isDefault }) =>
			isPending
			? 'pending'
			: isActive
			? 'active'
			: isDefault
			? 'active'
			: ''
		}>
		Future
	</NavLink>
	<NavLink to="/create-cat-form" id="large-center">
		Upon
	</NavLink>
	<NavLink to="/review-form" id="large-right">
		Review
	</NavLink>
	</div>
	<Outlet />

	<Routes>
		<Route exact path="/" element={<ShowReview />}></Route>
		<Route path="/create-cat-form" element={<CreateCatForm />}></Route>
		<Route path="/review-form" element={<ReviewCategory />}></Route>
		<Route path="/*" element={<ShowReview />}></Route>
	</Routes>
</div>
);
}
```

Seemingly much simpler than  watching for keystrokes, but working out the scss for this bad boy was no easy task. It would have been easier it I had just wanted to change the font color on a few links. Checkout the next frame.

``` css
@mixin large {
	width: 99%;
	height: 90%;
	box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.4),
	0 6px 10px 0 rgba(240, 7, 7, 0.19);
	border-top-right-radius: 7px;
	border-top-left-radius: 7px;
	text-align: center;
	vertical-align: middle;
	padding: 1%;
	margin: 1% 0;
}

#large-center {
	color: #cfad02;
	background-color: #ffdb00;
	left: 0.7%;
	@include large;
}

#large-right {
	color: #94480a;
	background-color: #c46210;
	left: 0.7%;
	@include large;
}

#large-left {
	color: #2e7d42;
	background-color: #0a6120;
	left: 0.7%;
	@include large;
}

#large-left.active {
	background-color: #8fd400;
	color: #000
}

#large-center.active {
	background-color: #fafa37;
	color: #000
}

#large-right.active {
	background-color: #ff9933;
	color: #000
}
```

