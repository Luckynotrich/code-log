
```python
import subprocess

return_code = subprocess.call(["python", "--version"])

if return_code == 0:
    print("Command executed successfully.")

else:
    print("Command failed with return code", return_code)
```
`subprocess.call()` is a function in the Python `subprocess` module that is used to run a command in a separate process and wait for it to complete. It returns the return code of the command, which is zero if the command was successful, and non-zero if it failed.

The `call()` function takes the same arguments as `run()`, including the args which specify the command to be run, and other optional arguments, such as `stdin`, `stdout`, `stderr`, `shell`, `cwd`, and `env`.

The standard output and error of the command are sent to the same `stdout` and `stderr` as the parent process unless you redirect them using `stdout` and `stderr` arguments.