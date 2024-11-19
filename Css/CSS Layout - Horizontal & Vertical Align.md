![[Pasted image 20240221102926.png]]  

## Center elements  
horizontally and vertically

___
![[Pasted image 20240221103138.png]]
## Center Align Elements
To horizontally center a block element (like <div>), use `margin: auto;`
Setting the width of the element will prevent it from stretching out to the edges of its container.
The element will then take up the specified width, and the remaining space will be split equally between the two margins:

### Example
```
.center {  margin: auto;  
  width: 50%;  
  border: 3px solid green;  
  padding: 10px;}
  ```
  
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_container)

**Note:** Center aligning has no effect if the `width` property is not set (or set to 100%).

___

## Center Align Text

To just center the text inside an element, use `text-align: center;`

This text is centered.

**Tip:** For more examples on how to align text, see the [CSS Text](https://www.w3schools.com/css/css_text.asp) chapter.

___

___

## Center an Image

To center an image, set left and right margin to `auto` and make it into a `block` element:

![Paris](https://www.w3schools.com/css/paris.jpg)

### Example
```
img {  display: block;  
  margin-left: auto;  
  margin-right: auto;  
  width: 40%;}
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_image)

___

## Left and Right Align - Using position

One method for aligning elements is to use `position: absolute;`:

In my younger and more vulnerable years my father gave me some advice that I've been turning over in my mind ever since.

### Example
```
.right {  position: absolute;  
  right: 0px;  
  width: 300px;  
  border: 3px solid #73AD21;  
  padding: 10px;}
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_pos)

**Note:** Absolute positioned elements are removed from the normal flow, and can overlap elements.

___

## Left and Right Align - Using float

Another method for aligning elements is to use the `float` property:

### Example
```
.right {  float: right;  
  width: 300px;  
  border: 3px solid #73AD21;  
  padding: 10px;}
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_float)

___

## The clearfix Hack

**Note:** If an element is taller than the element containing it, and it is floated, it will overflow outside of its container. You can use the "clearfix hack" to fix this (see example below).

### Without Clearfix

![](https://www.w3schools.com/howto/clearfix_prob.jpg)

### With Clearfix

![](https://www.w3schools.com/howto/clearfix_solution.jpg)

Then we can add the clearfix hack to the containing element to fix this problem:

### Example
```
.clearfix::after {  content: "";  
  clear: both;  
  display: table;}
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_clearfix)

___

## Center Vertically - Using padding

There are many ways to center an element vertically in CSS. A simple solution is to use top and bottom `padding`:

I am vertically centered.

To center both vertically and horizontally, use `padding` and `text-align: center`:

I am vertically and horizontally centered.

### Example
```
.center {  padding: 70px 0;  
  border: 3px solid green;  
  text-align: center;}
```
[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_padding2)

___

## Center Vertically - Using line-height

Another trick is to use the `line-height` property with a value that is equal to the `height` property:

I am vertically and horizontally centered.

### Example

.center {  line-height: 200px;  
  height: 200px;  
  border: 3px solid green;  
  text-align: center;}

  
.center p {  line-height: 1.5;  
  display: inline-block;  
  vertical-align: middle;}

[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_line-height)

___

## Center Vertically - Using position & transform

If `padding` and `line-height` are not options, another solution is to use positioning and the `transform` property:

I am vertically and horizontally centered.

### Example

.center {  height: 200px;  
  position: relative;  
  border: 3px solid green;}

.center p {  margin: 0;  
  position: absolute;  
  top: 50%;  
  left: 50%;  
  transform: translate(-50%, -50%);}

[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss_align_transform)

**Tip:** You will learn more about the transform property in our [2D Transforms Chapter](https://www.w3schools.com/css/css3_2dtransforms.asp).

___

## Center Vertically - Using Flexbox

You can also use flexbox to center things. Just note that flexbox is not supported in IE10 and earlier versions:

I am vertically and horizontally centered.

### Example

.center {  display: flex;  
  justify-content: center;  
  align-items: center;  
  height: 200px;  
  border: 3px solid green;}

[Try it Yourself »](https://www.w3schools.com/css/tryit.asp?filename=trycss3_align_flex)

**Tip:** You will learn more about Flexbox in our [CSS Flexbox Chapter](https://www.w3schools.com/css/css3_flexbox.asp).

___

  

W3schools Pathfinder

Track your progress - it's free!