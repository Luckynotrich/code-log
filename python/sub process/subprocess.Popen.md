
### python `subprocess`  `Popen`

```python
import subprocess

p = subprocess.Popen(["python", "--help"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)

output, errors = p.communicate()

print(output)

```

`subprocess.Popen()` is a lower-level interface to running sub processes, while `subprocess.run` is a higher-level wrapper around `Popen` that is intended to be more convenient to use.

`Popen` allows you to start a new process and interact with its standard input, output, and error streams. It returns a handle to the running process that can be used to wait for the process to complete, check its return code, or terminate it.

`run()` is a more convenient function that allows you to run a command and capture its output in a single call, without having to create a `Popen` object and manage the streams yourself. It also allows you to specify various options for running the command, such as whether to raise an exception if the command fails.

In general, you should use `run()` if you just need to run a command and capture its output and `Popen` if you need more control over the process, such as interacting with its input and output streams.

The `Popen` class takes the same arguments as `run()`, including the args that specify the command to be run and other optional arguments such as `stdin`, `stdout`, `stderr`, `shell`, `cwd`, and `env`. Also, the `Popen` class has several methods that allow you to interact with the process, such as `communicate()`, `poll()`, `wait()`, `terminate()`, and `kill()`.

```python
import subprocess

p = subprocess.Popen(["python", "--help"], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)

output, errors = p.communicate()

print(output)

```

Output:
```sh
usage: python [option] ... [-c cmd | -m mod | file | -] [arg] ...

Options and arguments (and corresponding environment variables):

-b     : issue warnings about str(bytes_instance), str(bytearray_instance)

         and comparing bytes/bytearray with str. (-bb: issue errors)

-B     : don't write .pyc files on import; also PYTHONDONTWRITEBYTECODE=x

-c cmd : program passed in as string (terminates option list)

-d     : debug output from parser; also PYTHONDEBUG=x

-E     : ignore PYTHON* environment variables (such as PYTHONPATH)

…
```

This will run the command `python –help` and create a new `Popen` object, which is stored in the variable `p`. The standard output and error of the command are captured using the `communicate()` method and stored in the variables output and errors, respectively.

`subprocess.Popen` is useful when you want more control over the process, such as sending input to it, receiving output from it, or waiting for it to complete.