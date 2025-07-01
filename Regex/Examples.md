**Escaping Special Characters:**

If you want to literally match a square bracket (e.g., `[`, `]`), you need to escape them with a backslash: `\[` and `\]`. 
- **Matching Everything Within Brackets:**
	    To capture the content inside brackets, you can use a combination of character classes and quantifiers. 
- **For example**, `\[[^\]]+\]` ` \[` will match a  open bracket, followed by`[^\]+` one or more characters that are not closing brackets, and then the `\]` closing bracket.

**To extract only the text within brackets** using regular expressions, you can use a regex pattern like `\[([^\]]*)\]`. This pattern matches an opening bracket `\[`, followed by `*(zero or more)`  characters except a closing bracket `([^\]]*)`, and then a closing bracket `\]`. The `([^\]]*)` part captures the text inside the brackets into a group, which you can then extract.

`(` and `)`: Define a capturing group, allowing you to extract the matched text inside the brackets.

get email addresses
![[Pasted image 20250610150146.png]]

phone numbers
![[Pasted image 20250610150519.png]]
