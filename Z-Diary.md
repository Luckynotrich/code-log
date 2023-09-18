8-24-2023 
I believe learning forms will be valuable. I don't know how valuable, but I think very.
I think learning react will be valuable. Same as above.

I learned about React [PropTypes](obsidian://open?vault=code-log&file=React%2FReact%20Prop-types). A way of implementing Variable Typing without a pre-processor.

8-25-2023
Leanne is coming to spend the weekend(Yay).
I got radio buttons to work with React-Hook-Form(RHF) yesterday. Today I have to add an [image](obsidian://open?vault=code-log&file=css%2FStyle%20Radio%20inputs) to represent the buttons.

Always check spelling and whether an import uses {} or default when an import is not found

8-28-2023
Installed Ubuntu Server 23.04 on [Media Server](obsidian://open?vault=code-log&file=Media%20Server) as well as kvm, libvirtd, 

9-7-2023
10 days Lapsed  minus 3 day weekend and one day feeling under the weather. Thought it was possible that I had COVID. Just Caffeine withdrawal.

Spent most of the time styling Future-Upon-Review
![[Pasted image 20230907150732.png]]
Just a note: This image was made in Gimp in which I have new experience 

Created ['How To use Font Awsome Icons in CSS'](obsidian://open?vault=code-log&file=css%2FHow%20to%20use%20Font%20Awesome%20Icons%20in%20CSS%20as%20background%20image) 
['A Checklist for choosing type-Fonts'](obsidian://open?vault=code-log&file=in%2FA%20checklist%20for%20choosing%20type%20%E2%80%93%20Fonts%20Knowledge%20-%20Google%20Fonts)
['Style Radio inputs'](obsidian://open?vault=code-log&file=css%2FStyle%20Radio%20inputs)

Yesterday and today: Spent time studying PASS
Created: [Read-Unread enhancement](obsidian://open?vault=code-log&file=PASS%2FRead-Unread%20enhancement)

9-7-2023
Star Rating color change working
Implemented Dark Light schemes(in FUR) using [Applying Dark Mode Styles in CSS by Ultimate Courses](https://ultimatecourses.com/blog/applying-dark-mode-styles-in-css)
Optional Technique by same: [Detecting Dark Mode in JavaScript](https://ultimatecourses.com/blog/detecting-dark-mode-in-javascript)

Made Pro/Con display optional(in Upon-Rreview) using: [LEARN REACT](https://react.dev/learn)/[Describing the UI](https://react.dev/learn/describing-the-ui)/ [Conditional Rendering](https://react.dev/learn/conditional-rendering)

9-11-2023
Completed Pro/Con optionality and added screen reset upon submit 

9-12-2023
Opened 'Git and GitHub' directory. Must master Git!
[Create GitHub Repo from the command line](obsidian://open?vault=code-log&file=Git%20and%20Github%2FCreate%20a%20GitHub%20repo%20from%20the%20command%20line)

9-13-2023
Added [Flex](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)to Large buttons in Future Self. 
Started a new webdev/[flex](https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox) directory for the tutorial linked here
Adding:: min-width: fit-content;
		and:: [overflow: scroll](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow); [CSS overflow Property](https://www.w3schools.com/cssref/pr_pos_overflow.php)
seemed to make the Large buttons and sections flex more consistently, but who knows. 
### I must keep notes AS I work,
not the following day as I am now.

9-14-2023
In an effort to handle refresh-redirect issues I ran 'npm run build' with the server pointed at
```
res.sendFile(path.join(__dirname, '../','upon-review','dist','build','index.html')) 
```
Only got the html without any js.
By adding routes to the build assets(dist, snowpack) I was able to get the built version running.
### New Note Style
===Researching how to handle screen resets and redirecting=== on button down
capture resets Ctrl-r and F5(worked in upon-review/App.jss)
[KeyboardEvent Value (keyCodes, metaKey, etc)](https://css-tricks.com/snippets/javascript/javascript-keycodes/)
```
const handleKeyDown = React.useCallback((e) => {
if((e.which || e.keyCode) == 116) {
e.preventDefault();/* disableKeyPressing(e); */
console.log('F5 is diabled now');
}

// Ctrl+R
if (e.ctrlKey && (e.which === 82) ) {
e.preventDefault();/* disableKeyPressing(e); */
console.log('Ctrl+R is pressed and refresh is diabled now');
}},[])

useEffect(() => {
window.addEventListener('keydown', handleKeyDown, true);
return () => {
window.removeEventListener('keydown', handleKeyDown, true);
};}, [handleKeyDown]);
```
[What Does $ Mean in JavaScript? Dollar Sign Operator in JS](https://www.freecodecamp.org/news/what-does-the-dollar-sign-mean-in-javascript/)

9-15-2023
### ===The above code was proved today===
[Detect Any KeyPress in React JS | Super Easy to Create KeyPress Based Applications](https://www.youtube.com/watch?v=D5SdvGMTEaU)
![[Pasted image 20230915085934.png]]
[How to add keyboard shortcuts to your React app](https://devtrium.com/posts/how-keyboard-shortcut)
![[Pasted image 20230915114900.png]]
### ===Experimenting with creating a router for review-form submit button.===
9-18-2023
This worked like a link, but didn't complete writing to the DB
![[Pasted image 20230918092138.png]]
Link didn't work
![[Pasted image 20230918092638.png]]
Ditto
![[Pasted image 20230918092907.png]]
