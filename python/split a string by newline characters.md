#### 1. Using `splitlines()`

- The `splitlines()` method is specifically designed to split a string into a list of lines, breaking at line boundaries.
- It handles various line break characters, including `\n`, `\r`, and `\r\n`.
- It does not include the line break characters in the resulting list.
- Example:
```python
     text = "Line 1\nLine 2\nLine 3"
     lines = text.splitlines()
     print(lines)  # Output: ['Line 1', 'Line 2', 'Line 3']
```

#### 2. Using `split('\n')`

- The `split()` method can also be used to split strings by a specified delimiter.
- Passing `\n` as the delimiter will split the string at every occurrence of the newline character.
- The newline characters will be removed from the resulting list.
- Example:
```python
     text = "Line 1\nLine 2\nLine 3"
     lines = text.split('\n')
     print(lines)  # Output: ['Line 1', 'Line 2', 'Line 3']
```

#### 3. Using `re.split('\n', string)`

- The `re.split()` function from the `re` module can also be used to split a string by a regular expression, including `\n`.
- Example:
```python
     import re
     text = "Line 1\nLine 2\nLine 3"
     lines = re.split('\n', text)
     print(lines)  # Output: ['Line 1', 'Line 2', 'Line 3']
```

#### Choosing the Right Method:

- If you want to split a string into lines and handle different types of line breaks, `splitlines()` is the most straightforward and recommended method.
- If you specifically want to split by the `\n` character and do not need to handle other types of line breaks, `split('\n')` is also suitable.
#### - `re.split('\n', string)` is useful when you need more complex pattern matching for splitting the string.

