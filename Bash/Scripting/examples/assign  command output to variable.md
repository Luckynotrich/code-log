use command substitution with `$()` or backticks `` ` ``. The syntax is `variable_name=$(command)` or `` variable_name=\`command\` `` . For example, to store the output of the `ls -l` command in a variable named `file_list`, you would use `file_list=$(ls -l)`. The variable can then be used or printed using `echo $file_list`.

If you need to capture both standard output (stdout) and standard error (stderr), you can redirect stderr to stdout using `2>&1` within the command substitution. For example, `output=$(command 2>&1)` will store both stdout and stderr in the `output` variable.

```sh
#!/bin/bash

# Assigning stdout to a variable
file_list=$(ls -l)
echo "File list: $file_list"

# Assigning stdout and stderr to a variable
error_output=$(command_that_may_fail 2>&1)
echo "Output and errors: $error_output"
```