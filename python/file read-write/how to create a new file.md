Using the `open()` function

The `open()` function is the primary way to create new files in Python. It takes two arguments:
- The file path (including the filename and extension).
- The mode in which to open the file.

Modes for creating files:
- `"x"`: Creates a new file, but fails if the file already exists.
- `"w"`: Creates a new file. If the file exists, it truncates the existing content.
- `"a"`: Creates a new file. If the file exists, it appends new content at the end

**Example using "x" mode:**
```python
try:
  f = open("new_file.txt", "x")
  f.write("This is a new file.")
  f.close()
except FileExistsError:
  print("File already exists.")
```

**Example using "w" mode:**
```python
f = open("new_file.txt", "w")
f.write("This is a new file.")
f.close()
```

**Using the `with` statement**
The `with` statement ensures that the file is properly closed after use.
```python
with open("new_file.txt", "w") as f:
    f.write("This is a new file.")
```

**Creating a file in a specific location**
To create a file in a specific directory, provide the full path to the `open()` function:
```python
import os

file_path = os.path.join("path", "to", "directory", "new_file.txt")
with open(file_path, "w") as f:
    f.write("This is a new file in a specific directory.")
```
