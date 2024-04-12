[MDN web docs](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)
```html
<div class="upEvents">
	<div class="upEventOne event" >
	<p>Launched today<br />
		Deadline May 15</p>
	</div>
	<div class="upEventTwo event">
		<h6>Hole-Earth Popup Putt Park, Mini Golf Homage to the Central Oregon Coast</h6> CALL FOR SUBMISSIONS<br />
		For more details: <a href="./open-call" target="_blank">open-call</a>
	</div>
		<div class="upEventThree">
			<a href="./dist/css/happenings/minigolf01.png" target="_blank">
				<img src="./images/upcoming/minigolf01.png" alt="Mini Golf Promo" />
			</a>
		</div>
</div>
```
for complete code see `/home/lucky/webdev/newledo/nef/dist/happenings.html`

```css
.upEvents {
	display: grid;
	grid-template-columns: repeat(7, 1fr);
	gap: 10px;
	grid-auto-rows: minmax(100px, auto);
	width: 1200px;
	margin: auto;
	align-items: start;
	font-family: "Montserrat", sans-serif;
}
.upEventOne {
	grid-column: 1 / 3;
	grid-row: 1;
	font-family: "Montserrat", sans-serif;
	font-weight: 600;
}

.upEventTwo {
	grid-column: 3 / 6;
	grid-row: 1;
}

.upEventThree {
	grid-column: 6/8;
	grid-row: 1;
	margin-right: 10px;
	padding: 10px;
}

@media screen and (max-width: 640px) {
.upEvents {
	grid-template-columns: 2fr 200px;
	grid-template-rows: masonry;
	padding-bottom: 10%;
	}

.upEventOne {
	align-items: end;
	padding-top: 3%;
	margin-top: 0%;
	grid-column: 1;
	grid-row: 2;
	}

.upEventTwo {
	align-items: end;
	grid-column: 1;
	grid-row: 1;
	}

.upEventThree {
	grid-column: 2;
	grid-row-end: span 2;
	}
}
```



