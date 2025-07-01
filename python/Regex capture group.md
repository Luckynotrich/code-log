Capture groups in Python's `re` module are defined using parentheses `()`. They allow you to extract specific portions of a matched string. 

Basic Capture Groups:

- Enclosing a part of your regex pattern in parentheses creates a capture group.
- The matched text within these parentheses can be accessed later.
- Groups are numbered from left to right, starting with 1. Group 0 usually represents the entire match.

Example:
```python
import re

text = "My name is John Doe."
pattern = r"My name is (\w+) (\w+)."
match = re.search(pattern, text)

if match:
    print(match.group(0))  # Output: My name is John Doe.
    print(match.group(1))  # Output: John
    print(match.group(2))  # Output: Doe
    print(match.groups())  # Output: ('John', 'Doe')
```

Named Capture Groups:

- You can assign names to capture groups using the syntax `(?P<name>...)`.
- This makes your code more readable, as you can access the group by its name instead of its index.
```python
import re

text = "User: john123, Level: 5"
pattern = r"User: (?P<username>\w+), Level: (?P<level>\d+)"
match = re.search(pattern, text)

if match:
    print(match.group("username"))  # Output: john123
    print(match.group("level"))    # Output: 5
    print(match.groupdict())    # Output: {'username': 'john123', 'level': '5'}
```

Non-Capturing Groups:

- Sometimes, you might need to group parts of your pattern for logical reasons but not to capture them.
- Use `(?:...)` to create a non-capturing group.
- These groups won't be included in the results of `match.groups()`.

Example:
```python
import re

text = "apple banana cherry"
pattern = r"(?:apple|banana) (cherry)"
match = re.search(pattern, text)

if match:
    print(match.group(0))  # Output: banana cherry
    print(match.group(1))  # Output: cherry
    print(match.groups())  # Output: ('cherry',)
```

Backreferences:

- You can refer to a previously captured group within the same pattern using `\1`, `\2`, etc.
- This is useful for finding repeated patterns.

Example:
```python
import re

text = "word word"
pattern = r"(\w+) \1"
match = re.search(pattern, text)

if match:
    print(match.group(0))  # Output: word word
```