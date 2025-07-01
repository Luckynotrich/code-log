[Python 3.13.4](https://docs.python.org/3/library/re.html)

- Key Concepts:
- **Meta characters:**
    Special characters that have specific meanings in regex, such as `.`, `^`, `$`, `*`, `+`, `?`, `[]`, `{}`, `|`, `\`, `()`.
- **Character Classes:**
    Predefined sets of characters, like `\d` (digits), `\w` (alphanumeric characters), `\s` (white space), `\D` (non-digits), `\W` (non-alphanumeric), `\S` (non-white space).
- **Quantifiers:**
    Specify how many times a character or group should appear: `*` (zero or more), `+` (one or more), `?` (zero or one), `{n}` (exactly n), `{n,}` (at least n), `{n,m}` (between n and m).
- **Anchors:**
    Match positions in the string: `^` (start of string), `$` (end of string), `\b` (word boundary), `\A` (start of string), `\Z` (end of string).
- **Grouping and Capturing:**
    Use parentheses `()` to group parts of a pattern and capture them for later use.
    

Basic Operations:
import the re module.
```python
    import re
```

Create a Regex Object.
```python
    pattern = re.compile(r"your_pattern")
```

**Search for patterns:**
- `re.search(pattern, string)`: Searches the entire string for the first occurrence of the pattern. 
- `re.match(pattern, string)`: Checks for a match only at the beginning of the string. 
- `re.fullmatch(pattern, string)`: Checks if the entire string matches the pattern.
- `re.findall(pattern, string)`: Returns all non-overlapping matches as a list of strings.
- `re.finditer(pattern, string)`: Returns an iterator of match objects for all matches.

- **Modify strings:**
- `re.sub(pattern, replacement, string)`: Replaces all occurrences of the pattern with the replacement string.
- `re.split(pattern, string)`: Splits the string into a list at each occurrence of the pattern.
```python
import re

text = "The quick brown fox jumps over the lazy dog."

# Find all words starting with 't'
matches = re.findall(r'\bt\w+', text)
print(matches) # Output: ['the', 'the']

# Replace 'fox' with 'cat'
new_text = re.sub(r'fox', 'cat', text)
print(new_text) # Output: The quick brown cat jumps over the lazy dog.
```