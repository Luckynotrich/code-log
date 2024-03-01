Here is a simple quick way to use icons from Font Awesome as a “background-image” using CSS.

You need to get the code of the symbol of Font Awesome. The easiest way is to use your browser inspector on the the icon you want to use and copy the code, in my example it’s the little star icon using the code “\\f005”.

Add “position: relative;” to your container and use the :before (or :after) property to call your symbole.

```css
.button {
  padding-left: 32px;
  position: relative;
}
.button:before {
  position: absolute;
  font-family: 'FontAwesome';
  top: 0;
  left: 10px;
  content: "\f005";
}
```
#### This didn't work 
