# [How TO - Change a Class](https://www.w3schools.com/howto/howto_js_change_class.asp)



<div id="myDIV" class="mystyle">  
This is a DIV element.  
</div>  
  ```js
<script>  
function myFunction() {  
  const element = document.getElementById("myDIV");  // Get the DIV element  
  element.classList.remove("mystyle"); // Remove mystyle class from DIV  
  element.classList.add("newone"); // Add newone class to DIV  
}  
</script>
```

