# Markdown Cheat Sheet

Thanks for visiting [The Markdown Guide](https://www.markdownguide.org)!

This Markdown cheat sheet provides a quick overview of all the Markdown syntax elements. It can’t cover every edge case, so if you need more information about any of these elements, refer to the reference guides for [basic syntax](https://www.markdownguide.org/basic-syntax) and [extended syntax](https://www.markdownguide.org/extended-syntax).

## Basic Syntax

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

# H1
## H2
### H3

### Bold

**bold text**

### Italic

*italicized text*

### Blockquote

> blockquote

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- First item
- Second item
- Third item

### Code

`code`

### Horizontal Rule

---

### Link

[Markdown Guide](https://www.markdownguide.org)

### Image

![alt text](https://www.markdownguide.org/assets/images/tux.png)

## Extended Syntax

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

| Syntax | Description |
| ----------- | ----------- |
| Header | Title |
| Paragraph | Text |

### Fenced Code Block

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Footnote

Here's a sentence with a footnote. [^1]

[^1]: This is the footnote.

### Heading ID

### My Great Heading {#custom-id}

### Definition List

term
: definition

### Strikethrough

~~The world is flat.~~

### Task List

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

### Emoji

That is so funny! :joy:

(See also [Copying and Pasting Emoji](https://www.markdownguide.org/extended-syntax/#copying-and-pasting-emoji))

### Highlight

I need to highlight these ==very important words==.

### Subscript
H~2~O (This does NOT work in Obsidian)
Obsidian $_t$$_m$ (This does work in Obsidian using`$_t$$_m$ `)
$\pu{Obsidian _{tm}}$ (Using `$\pu{Obsidian _{tm}}$` seems to change the font)


### Superscript
X^2^ (This does NOT work in Obsidian)
Obsidian$^T$$^M$    (This does work in Obsidian using `$^T$$^M$`)
$\pu{Obsidian ^{TM}}$ (Using `$\pu{Obsidian ^{TM}}$`)

The right way to represent what you want is to put both quantity and unit inside the `\pu` command (“pu” stands for “physical unit”):

```markdown
$\pu{100 m2}$
```

which renders as
#####  $\pu{100 m2}$

More examples:

```markdown
$\pu{1.23 kg.m^{-3}}$

$\pu{8.31432e3 N.m.kmol^{-1}.K^{-1}}$
```
##### $\pu{1.23 kg.m^{-3}}$
(above edited to demonstrate subtext)
#####  $\pu{8.31432e3 N.m.kmol^{-1}.K_{-1}}$



1. You can use html tag `<sup>your text</sup>`. But this is only practical for occasional use.   A more practical way is create a template using Templater plugin syntax:

```css
<sup><% tp.file.selection() %></sup>
```

Then create a shortcut/hotkey (via Templater plugin settings) to this template. To use it you select the wanted text and apply the shortcut.

2. Second way - install the plugin cMenu.

EDIT: In 1. for “subscripts” create another template with `<sub><% tp.file.selection() %></sub>`


