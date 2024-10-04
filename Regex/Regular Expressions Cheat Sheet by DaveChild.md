
# Regular Expressions Cheat Sheet by DaveChild - Download free from Cheatography - Cheatography.com: Cheat Sheets For Every Occasion

> ## Excerpt
> A quick reference guide for regular expressions (regex), including symbols, ranges, grouping, assertions and some sample patterns to get you started.

---
### Anchors

<table id="cheat_sheet_output_table"><tbody><tr><td><p>^</p></td><td><p>Start of string, or start of line in multi-line pattern</p></td></tr><tr><td><p>\A</p></td><td><p>Start of string</p></td></tr><tr><td><p>$</p></td><td><p>End of string, or end of line in multi-line pattern</p></td></tr><tr><td><p>\Z</p></td><td><p>End of string</p></td></tr><tr><td><p>\b</p></td><td><p>Word boundary</p></td></tr><tr><td><p>\B</p></td><td><p>Not word boundary</p></td></tr><tr><td><p>\&lt;</p></td><td><p>Start of word</p></td></tr><tr><td><p>\&gt;</p></td><td><p>End of word</p></td></tr></tbody></table>

### Character Classes

<table id="cheat_sheet_output_table"><tbody><tr><td><p>\c</p></td><td><p>Control character</p></td></tr><tr><td><p>\s</p></td><td><p>White space</p></td></tr><tr><td><p>\S</p></td><td><p>Not white space</p></td></tr><tr><td><p>\d</p></td><td><p>Digit</p></td></tr><tr><td><p>\D</p></td><td><p>Not digit</p></td></tr><tr><td><p>\w</p></td><td><p>Word</p></td></tr><tr><td><p>\W</p></td><td><p>Not word</p></td></tr><tr><td><p>\x</p></td><td><p>Hexadecimal digit</p></td></tr><tr><td><p>\O</p></td><td><p>Octal digit</p></td></tr></tbody></table>

### POSIX

<table id="cheat_sheet_output_table"><tbody><tr><td><p>[:upper:]</p></td><td><p>Upper case letters</p></td></tr><tr><td><p>[:lower:]</p></td><td><p>Lower case letters</p></td></tr><tr><td><p>[:alpha:]</p></td><td><p>All letters</p></td></tr><tr><td><p>[:alnum:]</p></td><td><p>Digits and letters</p></td></tr><tr><td><p>[:digit:]</p></td><td><p>Digits</p></td></tr><tr><td><p>[:xdigit:]</p></td><td><p>Hexadecimal digits</p></td></tr><tr><td><p>[:punct:]</p></td><td><p>Punctuation</p></td></tr><tr><td><p>[:blank:]</p></td><td><p>Space and tab</p></td></tr><tr><td><p>[:space:]</p></td><td><p>Blank characters</p></td></tr><tr><td><p>[:cntrl:]</p></td><td><p>Control characters</p></td></tr><tr><td><p>[:graph:]</p></td><td><p>Printed characters</p></td></tr><tr><td><p>[:print:]</p></td><td><p>Printed characters and spaces</p></td></tr><tr><td><p>[:word:]</p></td><td><p>Digits, letters and underscore</p></td></tr></tbody></table>

### Assertions

<table id="cheat_sheet_output_table"><tbody><tr><td><p>?=</p></td><td><p>Lookahead assertion</p></td></tr><tr><td><p>?!</p></td><td><p>Negative lookahead</p></td></tr><tr><td><p>?&lt;=</p></td><td><p>Lookbehind assertion</p></td></tr><tr><td><p>?!= or ?&lt;!</p></td><td><p>Negative lookbehind</p></td></tr><tr><td><p>?&gt;</p></td><td><p>Once-only Subexpression</p></td></tr><tr><td><p>?()</p></td><td><p>Condition [if then]</p></td></tr><tr><td><p>?()|</p></td><td><p>Condition [if then else]</p></td></tr><tr><td><p>?#</p></td><td><p>Comment</p></td></tr></tbody></table>

 

### Quantifiers

<table id="cheat_sheet_output_table"><tbody><tr><td><p>*</p></td><td><p>0 or more</p></td><td><p>{3}</p></td><td><p>Exactly 3</p></td></tr><tr><td><p>+</p></td><td><p>1 or more</p></td><td><p>{3,}</p></td><td><p>3 or more</p></td></tr><tr><td><p>?</p></td><td><p>0 or 1</p></td><td><p>{3,5}</p></td><td><p>3, 4 or 5</p></td></tr></tbody></table>

Add a ? to a quantifier to make it ungreedy.

### Escape Sequences

<table id="cheat_sheet_output_table"><tbody><tr><td><p>\</p></td><td><p>Escape following character</p></td></tr><tr><td><p>\Q</p></td><td><p>Begin literal sequence</p></td></tr><tr><td><p>\E</p></td><td><p>End literal sequence</p></td></tr></tbody></table>

"Escaping" is a way of treating characters which have a special meaning in regular expressions literally, rather than as special characters.

### Common Metacharacters

<table id="cheat_sheet_output_table"><tbody><tr><td><p>^</p></td><td><p>[</p></td><td><p>.</p></td><td><p>$</p></td></tr><tr><td><p>{</p></td><td><p>*</p></td><td><p>(</p></td><td><p>\</p></td></tr><tr><td><p>+</p></td><td><p>)</p></td><td><p>|</p></td><td><p>?</p></td></tr><tr><td><p>&lt;</p></td><td colspan="3"><p>&gt;</p></td></tr></tbody></table>

The escape character is usually \\

### Special Characters

<table id="cheat_sheet_output_table"><tbody><tr><td><p>\n</p></td><td><p>New line</p></td></tr><tr><td><p>\r</p></td><td><p>Carriage return</p></td></tr><tr><td><p>\t</p></td><td><p>Tab</p></td></tr><tr><td><p>\v</p></td><td><p>Vertical tab</p></td></tr><tr><td><p>\f</p></td><td><p>Form feed</p></td></tr><tr><td><p>\xxx</p></td><td><p>Octal character xxx</p></td></tr><tr><td><p>\xhh</p></td><td><p>Hex character hh</p></td></tr></tbody></table>

 

### Groups and Ranges

<table id="cheat_sheet_output_table"><tbody><tr><td><p>.</p></td><td><p>Any character except new line (\n)</p></td></tr><tr><td><p>(a|b)</p></td><td><p>a or b</p></td></tr><tr><td><p>(...)</p></td><td><p>Group</p></td></tr><tr><td><p>(?:...)</p></td><td><p>Passive (non-capturing) group</p></td></tr><tr><td><p>[abc]</p></td><td><p>Range (a or b or c)</p></td></tr><tr><td><p>[^abc]</p></td><td><p>Not (a or b or c)</p></td></tr><tr><td><p>[a-q]</p></td><td><p>Lower case letter from a to q</p></td></tr><tr><td><p>[A-Q]</p></td><td><p>Upper case letter from A to Q</p></td></tr><tr><td><p>[0-7]</p></td><td><p>Digit from 0 to 7</p></td></tr><tr><td><p>\x</p></td><td><p>Group/subpattern number "x"</p></td></tr></tbody></table>

### Pattern Modifiers

<table id="cheat_sheet_output_table"><tbody><tr><td><p>g</p></td><td><p>Global match</p></td></tr><tr><td><p>i&nbsp;*</p></td><td><p>Case-insensitive</p></td></tr><tr><td><p>m&nbsp;*</p></td><td><p>Multiple lines</p></td></tr><tr><td><p>s&nbsp;*</p></td><td><p>Treat string as single line</p></td></tr><tr><td><p>x&nbsp;*</p></td><td><p>Allow comments and whitespace in pattern</p></td></tr><tr><td><p>e&nbsp;*</p></td><td><p>Evaluate replacement</p></td></tr><tr><td><p>U&nbsp;*</p></td><td><p>Ungreedy pattern</p></td></tr></tbody></table>

### String Replacement

<table id="cheat_sheet_output_table"><tbody><tr><td><p>$n</p></td><td><p>nth non-passive group</p></td></tr><tr><td><p>$2</p></td><td><p>"xyz" in /^(abc(xyz))$/</p></td></tr><tr><td><p>$1</p></td><td><p>"xyz" in /^(?:abc)(xyz)$/</p></td></tr><tr><td><p>$`</p></td><td><p>Before matched string</p></td></tr><tr><td><p>$'</p></td><td><p>After matched string</p></td></tr><tr><td><p>$+</p></td><td><p>Last matched string</p></td></tr><tr><td><p>$&amp;</p></td><td><p>Entire matched string</p></td></tr></tbody></table>

Some regex implementations use \\ instead of $.
