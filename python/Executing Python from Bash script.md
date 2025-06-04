
### 1. Direct Execution:

- Use the `python` command followed by the path to your Python script.
- Example:
```sh
     #!/bin/bash
     python /path/to/your/script.py
```

Ensure the Python executable is in your system's `PATH` environment variable.

### 2. Inline Python Code:
- Use the `-c` option with the `python` command to execute Python code directly in the Bash script.
- Example:
```sh
     #!/bin/bash
     python -c "print('Hello from Python!')"
```

- For multi-line code, use a here-string:
```sh
     #!/bin/bash
     python - <<'END_PYTHON'
     print("Hello,")
     print("This is a multi-line Python script")
     END_PYTHON
```

### 3. Passing Arguments:

Pass arguments after the Python script path in the Bash script and Example.
```sh
     #!/bin/bash
     python /path/to/your/script.py arg1 arg2
```

- Access these arguments in your Python script using `sys.argv`
```python
     import sys
     print(sys.argv)
```

### 4. Using `env`:
- Use `#!/usr/bin/env python` at the beginning of your Python script to let the environment find the correct Python executable.
- This approach is more portable.
- Example:
```python
     #!/usr/bin/env python
     print("Hello from Python!")
```

**Make the Python script executable using `chmod +x your_script.py`, then run it directly.**

### 5. Setting `PYTHONPATH`:

- If your Python script relies on external modules, set the `PYTHONPATH` environment variable.
- Example:
```sh
     #!/bin/bash
     export PYTHONPATH=/path/to/your/modules
     python /path/to/your/script.py
```

### 6. Using `subprocess`:
- From within a Python script, you can use the `subprocess` module to run Bash commands.
- Example:
```python
     import subprocess
     subprocess.run(['bash', '-c', 'ls -l'])
```