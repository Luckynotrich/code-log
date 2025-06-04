### python `subprocess` check_output
```python
import subprocess

try:

    output = subprocess.check_output(["python", "--version"], text=True)

    print(output)

except subprocess.CalledProcessError as e:

    print(f"Command failed with return code {e.returncode}")

```

`check_output` is a function in the `subprocess` module that is similar to `run()`, but it only returns the standard output of the command, and raises a `CalledProcessError` exception if the return code is non-zero.

The `check_output()` function takes the same arguments as `run()`, including the args which specify the command to be run, and other optional arguments, such as `stdin`, `stderr`, `shell`, `cwd`, and `env`.

The `check_output()` function returns the standard output of the command as a bytes object or string, if `text=True` is passed.