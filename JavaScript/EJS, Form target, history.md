
The code below is `/home/lucky/webdev/future-upon-review/ur-backend/views/login.ejs`
It uses flash and ejs to display messages. On Submit in display the response content in a new tab using `target="_blank" ` in the form tag and it send it window back in browser history 10 second after the `onClick` event
```js
<!DOCTYPE html>
<html>
	<head>
		<%- include('./partials/head'); %>
	</head>
	<meta name="viewport" content="width=device-width, initial-scale=1">
<body style="display: grid;grid-template-columns: auto; max-width: 10rem;">
	<div><h1>Login</h1>
	<ul style="decoration: none">
	<% if(messages.success_msg1) {%>
		<li><%= messages.success_msg1 %></li>
	<% } %>
	<% if(messages.success_msg2) {%>
		<li><%= messages.success_msg2 %></li>
	<%}else {%><li>&nbsp&nbsp&nbsp&nbsp&nbsp</li> <% } %>
	<% if(messages.error){ %>
		<li><%= messages.error %></li>
	<%}else {%><li>&nbsp&nbsp&nbsp&nbsp&nbsp</li> <% } %>
	</ul>
	</div>
	<form action="/users/login" method="post" target="_blank">
		<div style="margin-left:2rem;">
		<label for="email">Email:</label>
		<input type="email" id="email" name="email" required>
		</div>
		<div style="display: flex;flex-direction: column;margin-left:2rem;">
		<label for="password">Password:</label>
		<input type="password" id="password" name="password" required>
		</div>
		<div style="margin-left: 2rem;">
		<input type="submit" value="Login" onclick="setTimeout(window.history.back(1),10000)" >
		</div>
	</form>
	<div style="margin-left: 2rem;">
	<a href="/signup">Need to Sign up?</a>
<footer>
	<%- include('./partials/home_footer'); %>
</footer>
</div>
</body>
</html>
```