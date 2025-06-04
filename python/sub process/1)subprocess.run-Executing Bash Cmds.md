## [Python docs 3.10.17](https://docs.python.org/3.10/library/subprocess.html)
### Using `subprocess`:

- From within a Python script, you can use the `subprocess` module to run Bash commands.
- Example:
```python
     import subprocess
     subprocess.run(['bash', '-c', 'ls -l'])
```

## Python `subprocess` Examples 

Let's now take a look at some Python `subprocess` examples.

### python `subprocess` run

The `subprocess.run()` method is a convenient way to run a `subprocess` and wait for it to complete. It lets you choose the command to run and add options like arguments, environment variables, and input/output redirections. Once the `subprocess` is started, the `run()` method blocks until the `subprocess` completes and returns a `CompletedProcess` object, which contains the return code and output of the `subprocess`.

The `subprocess.run()` method takes several arguments, some of which are:

- `args`: The command to run and its arguments, passed as a list of strings.
    
- `capture_output`: When set to True, will capture the standard output and standard error.
    
- `text`: When set to True, will return the stdout and stderr as string, otherwise as bytes.
    
- `check`: a boolean value that indicates whether to check the return code of the `subprocess`, if check is true and the return code is non-zero, then `subprocess`  `CalledProcessError` is raised.
    
- `timeout`: A value in seconds that specifies how long to wait for the `subprocess` to complete before timing out.
    
- `shell`: A boolean value that indicates whether to run the command in a shell. This means that the command is passed as a string, and shell-specific features, such as wildcard expansion and variable substitution, can be used.
    

The `subprocess.run()` method also returns a `CompletedProcess` object, which contains the following attributes:

- `args`: The command and arguments that were run.
    
- `returncode`: The return code of the `subprocess`.
    
- `stdout`: The standard output of the `subprocess`, as a bytes object.
    
- `stderr`: The standard error of the `subprocess`, as a bytes object.

#### Example 1: Running shell commands:
```python
import subprocess

result = subprocess.run(["ls -l"], shell=True, capture_output=True, text=True)

print(result.stdout)

```

Windows users replace `ls -l` with `dir`

#### Example 2: Running Python scripts:

You can also run a python script using the `subprocess.run()` method. Let’s start by creating a simple Python script in `.py` file
```python
print(“This is the output from subprocess module”)

```

Save this file as `my_python_file.py`. Now, you can use the `subprocess` module to run this file:
```python
import subprocess

result = subprocess.run(["python", "my_python_file.py"], capture_output=True, text=True)

print(result.stdout)

```

Output:
```sh
This is the output from subprocess module

```

#### Example 4: Using the check argument

The check argument is an optional argument of the `subprocess.run()` function in the Python subprocess module. It is a boolean value that controls whether the function should check the return code of the command being run.

When check is set to `True`, the function will check the return code of the command and raise a `CalledProcessError` exception if the return code is non-zero. The exception will have the return code, `stdout`, `stderr`, and `command` as attributes.

When check is set to `False` (default), the function will not check the return code and will not raise an exception, even if the command fails.

```python
import subprocess

result = subprocess.run(["python", "file_donot_exist.py"], capture_output=True, text=True, check=True)

print(result.stdout)

print(result.stderr)

```

Output:
```sh
---------------------------------------------------------------------------

CalledProcessError                        Traceback (most recent call last)

<ipython-input-81-503b60184db8> in <module>

      1 import subprocess

----> 2 result = subprocess.run(["python", "file_donot_exist.py"], capture_output=True, text=True, check=True)

      3 print(result.stdout)

      4 print(result.stderr)

~\anaconda3\lib\subprocess.py in run(input, capture_output, timeout, check, *popenargs, **kwargs)

    514         retcode = process.poll()

    515         if check and retcode:

--> 516             raise CalledProcessError(retcode, process.args,

    517                                      output=stdout, stderr=stderr)

    518     return CompletedProcess(process.args, retcode, stdout, stderr)

CalledProcessError: Command '['python', 'file_donot_exist.py']' returned non-zero exit status 2.
```

**Notice that the command failed** because `file_donot_exist.py` does not exist. As opposed to when you set `check=True`, your process won’t fail; instead, you will get the error message in `stdout`.
```python
import subprocess

result = subprocess.run(["python", "my_python_file2.py"], capture_output=True, text=True, check=False)

print(result.stdout)

print(result.stderr)

```

