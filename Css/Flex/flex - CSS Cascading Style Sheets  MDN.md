###### Baseline Widely available
Local play area `/home/lucky/webdev/flex/`
The **`flex`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) [shorthand property](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) sets how a flex _item_ will grow or shrink to fit the space available in its flex container.

## [Try it](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#try_it)

## [Constituent properties](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#constituent_properties)

This property is a shorthand for the following CSS properties:

-   [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow)
-   [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink)
-   [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis)

## [Syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#syntax)
![[Pasted image 20240221102106.png]]


The `flex` property may be specified using one, two, or three values.

-   **One-value syntax:** the value must be one of:
    -   a valid value for [`<flex-grow>`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow): then the shorthand expands to `flex: <flex-grow> 1 0`.
    -   a valid value for [`<flex-basis>`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis): then the shorthand expands to `flex: 1 1 <flex-basis>`.
    -   the keyword `none` or one of the global keywords.
-   **Two-value syntax:**
    -   The first value must be a valid value for [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow).
    -   The second value must be one of:
        -   a valid value for [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink): then the shorthand expands to `flex: <flex-grow> <flex-shrink> 0`.
        -   a valid value for [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis): then the shorthand expands to `flex: <flex-grow> 1 <flex-basis>`.
-   **Three-value syntax:** the values must be in the following order:
    1.  a valid value for [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow).
    2.  a valid value for [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink).
    3.  a valid value for [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis).

### [Values](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#values)

[`initial`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#initial)

The item is sized according to its `width` and `height` properties. It shrinks to its minimum size to fit the container, but does not grow to absorb any extra free space in the flex container. This is equivalent to setting "`flex: 0 1 auto`".

[`auto`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#auto)

The item is sized according to its `width` and `height` properties, but grows to absorb any extra free space in the flex container, and shrinks to its minimum size to fit the container. This is equivalent to setting "`flex: 1 1 auto`".

[`none`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#none)

The item is sized according to its `width` and `height` properties. It is fully inflexible: it neither shrinks nor grows in relation to the flex container. This is equivalent to setting "`flex: 0 0 auto`".

[`<'flex-grow'>`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#flex-grow)

Defines the [`flex-grow`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow) of the flex item. Negative values are considered invalid. Defaults to `1` when omitted. (initial is `0`)

[`<'flex-shrink'>`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#flex-shrink)

Defines the [`flex-shrink`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink) of the flex item. Negative values are considered invalid. Defaults to `1` when omitted. (initial is `1`)

[`<'flex-basis'>`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#flex-basis)

Defines the [`flex-basis`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis) of the flex item. A preferred size of `0` must have a unit to avoid being interpreted as a flexibility. Defaults to `0` when omitted. (initial is `auto`)

## [Description](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#description)

For most purposes, authors should set `flex` to one of the following values: `auto`, `initial`, `none`, or a positive unitless number. To see the effect of these values, try resizing the flex containers below:

By default flex items don't shrink below their minimum content size. To change this, set the item's [`min-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-width) or [`min-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-height).

## [Formal definition](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#formal_definition)

<table><tbody><tr><th scope="row"><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/initial_value">Initial value</a></th><td>as each of the properties of the shorthand:<br><ul><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow"><code>flex-grow</code></a>: <code>0</code></li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink"><code>flex-shrink</code></a>: <code>1</code></li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis"><code>flex-basis</code></a>: <code>auto</code></li></ul></td></tr><tr><th scope="row">Applies to</th><td>flex items, including in-flow pseudo-elements</td></tr><tr><th scope="row"><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Inheritance">Inherited</a></th><td>no</td></tr><tr><th scope="row"><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/computed_value">Computed value</a></th><td>as each of the properties of the shorthand:<br><ul><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow"><code>flex-grow</code></a>: as specified</li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink"><code>flex-shrink</code></a>: as specified</li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis"><code>flex-basis</code></a>: as specified, but with relative lengths converted into absolute lengths</li></ul></td></tr><tr><th scope="row">Animation type</th><td>as each of the properties of the shorthand:<br><ul><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-grow"><code>flex-grow</code></a>: a <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/number#interpolation" title="Values of the <number> CSS data type are interpolated as real, floating-point, numbers.">number</a></li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-shrink"><code>flex-shrink</code></a>: a <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/number#interpolation" title="Values of the <number> CSS data type are interpolated as real, floating-point, numbers.">number</a></li><li><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis"><code>flex-basis</code></a>: a <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/length#interpolation" title="Values of the <length> CSS data type are interpolated as real, floating-point numbers.">length</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/percentage#interpolation" title="Values of the <percentage> CSS data type are interpolated as real, floating-point numbers.">percentage</a> or calc();</li></ul></td></tr></tbody></table>

## [Formal syntax](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#formal_syntax)

```
<span id="flex">flex = </span><br>  <span>none</span>                                                <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Value_definition_syntax#single_bar" title="Single bar: exactly one of the entities must be present">|</a><br>  <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Value_definition_syntax#brackets" title="Brackets: enclose several entities, combinators, and multipliers to transform them as a single component">[</a> <span>&lt;'flex-grow'&gt;</span> <span>&lt;'flex-shrink'&gt;</span><a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Value_definition_syntax#question_mark" title="Question mark: the entity is optional">?</a> <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Value_definition_syntax#double_bar" title="Double bar: one or several of the entities must be present, in any order">||</a> <span>&lt;'flex-basis'&gt;</span> <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/Value_definition_syntax#brackets" title="Brackets: enclose several entities, combinators, and multipliers to transform them as a single component">]</a>  <br><br>
```

## [Examples](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#examples)

### [Setting flex: auto](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#setting_flex_auto)

This example shows how a flex item with `flex: auto` grows to absorb any free space in the container.

#### HTML

```
<span><span><span>&lt;</span>div</span> <span>id</span><span><span>=</span><span>"</span>flex-container<span>"</span></span><span>&gt;</span></span>
  <span><span><span>&lt;</span>div</span> <span>id</span><span><span>=</span><span>"</span>flex-auto<span>"</span></span><span>&gt;</span></span>flex: auto (click to toggle raw box)<span><span><span>&lt;/</span>div</span><span>&gt;</span></span>
  <span><span><span>&lt;</span>div</span> <span>id</span><span><span>=</span><span>"</span>flex-initial<span>"</span></span><span>&gt;</span></span>flex: initial<span><span><span>&lt;/</span>div</span><span>&gt;</span></span>
<span><span><span>&lt;/</span>div</span><span>&gt;</span></span>
```

#### CSS

```
<span>#flex-container</span> <span>{</span>
  <span>display</span><span>:</span> flex<span>;</span>
  <span>font-family</span><span>:</span> Consolas<span>,</span> Arial<span>,</span> sans-serif<span>;</span>
<span>}</span>

<span>#flex-container &gt; div</span> <span>{</span>
  <span>padding</span><span>:</span> 1rem<span>;</span>
<span>}</span>

<span>#flex-auto</span> <span>{</span>
  <span>flex</span><span>:</span> auto<span>;</span>
  <span>border</span><span>:</span> 1px solid #f00<span>;</span>
<span>}</span>

<span>#flex-initial</span> <span>{</span>
  <span>border</span><span>:</span> 1px solid #000<span>;</span>
<span>}</span>
```

#### JavaScript

```
<span>const</span> flexAuto <span>=</span> document<span>.</span><span>getElementById</span><span>(</span><span>"flex-auto"</span><span>)</span><span>;</span>
<span>const</span> flexInitial <span>=</span> document<span>.</span><span>getElementById</span><span>(</span><span>"flex-initial"</span><span>)</span><span>;</span>
flexAuto<span>.</span><span>addEventListener</span><span>(</span><span>"click"</span><span>,</span> <span>(</span><span>)</span> <span>=&gt;</span> <span>{</span>
  flexInitial<span>.</span>style<span>.</span>display <span>=</span>
    flexInitial<span>.</span>style<span>.</span>display <span>===</span> <span>"none"</span> <span>?</span> <span>"block"</span> <span>:</span> <span>"none"</span><span>;</span>
<span>}</span><span>)</span><span>;</span>
```

#### Result

The flex container contains two flex items:

-   "flex: auto" has a `flex` value of [`auto`](https://developer.mozilla.org/en-US/docs/Web/CSS/auto)
-   "flex: initial" has a `flex` value of [`initial`](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#initial)

The "flex: initial" item takes up as much space as its width requires, but does not expand to take up any more space. All the remaining space is taken up by "flex: auto".

When you click "flex: auto", we set "flex: initial"'s [`display`](https://developer.mozilla.org/en-US/docs/Web/CSS/display) property to `none`, removing it from the layout. The "flex: auto" item then expands to occupy all the available space in the container.

## [Specifications](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#specifications)

| Specification |
| --- |
| [CSS Flexible Box Layout Module Level 1  
<small># flex-property</small>](https://drafts.csswg.org/css-flexbox/#flex-property) |

## [Browser compatibility](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#browser_compatibility)

[Report problems with this compatibility data on GitHub](https://github.com/mdn/browser-compat-data/issues/new?mdn-url=https%3A%2F%2Fdeveloper.mozilla.org%2Fen-US%2Fdocs%2FWeb%2FCSS%2Fflex&metadata=%3C%21--+Do+not+make+changes+below+this+line+--%3E%0A%3Cdetails%3E%0A%3Csummary%3EMDN+page+report+details%3C%2Fsummary%3E%0A%0A*+Query%3A+%60css.properties.flex%60%0A*+Report+started%3A+2024-02-21T18%3A14%3A53.810Z%0A%0A%3C%2Fdetails%3E&title=css.properties.flex+-+%3CSUMMARIZE+THE+PROBLEM%3E&template=data-problem.yml "Report an issue with this compatibility data")

|  | desktop | mobile |
| --- | --- | --- |
|  | 
Chrome

 | 

Edge

 | 

Firefox

 | 

Opera

 | 

Safari

 | 

Chrome Android

 | 

Firefox for Android

 | 

Opera Android

 | 

Safari on iOS

 | 

Samsung Internet

 | 

WebView Android

 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 

`flex`

 |  |  |  |  |  |  |  |  |  |  |  |

### Legend

Tip: you can click/tap on a cell for more information.

Full support

Full support

Requires a vendor prefix or different name for use.

Has more compatibility info.

## [See also](https://developer.mozilla.org/en-US/docs/Web/CSS/flex#see_also)