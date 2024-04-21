
# [`parseInt()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt)

```
parseInt(string)
parseInt(string, radix)
```


### [Parameters](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#parameters)

[`string`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#string)

A string starting with an integer. Leading [whitespace](https://developer.mozilla.org/en-US/docs/Glossary/Whitespace) in this argument is ignored.

[`radix`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#radix) Optional

An integer between `2` and `36` that represents the _radix_ (the base in mathematical numeral systems) of the `string`. It is converted to a [32-bit integer](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#fixed-width_number_conversion); if it's nonzero and outside the range of [2, 36] after conversion, the function will always return `NaN`. If `0` or not provided, the radix will be inferred based on `string`'s value. Be careful — this does _not_ always default to `10`! The [description below](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#description) explains in more detail what happens when `radix` is not provided.

### [Return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/parseInt#return_value)

An integer parsed from the given `string`, or [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) when

- the `radix` as a 32-bit integer is smaller than `2` or bigger than `36`, or
- the first non-whitespace character cannot be converted to a number.