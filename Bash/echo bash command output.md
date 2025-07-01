The `echo` command in Bash is primarily used to display text or variables. To capture and display the output of another command, you can use command substitution. Here are the common methods:

1. Using `$(command)`:
This is the preferred method for command substitution. The command inside the parentheses is executed, and its output replaces the entire `$(...)` expression.

```sh
echo $(ls -l)
```

2. Using Back ticks `` `command` ``:
Back ticks are an older way to achieve the same command substitution. However, `$(...)` is generally preferred because it is easier to nest and read.

```sh
echo `date`
```

3. Storing command output in a variable:
You can store the output of a command into a variable and then echo the variable
```sh
output=$(whoami)
echo "Current user: $output"
```

4. Printing the command itself before execution:
You can use `set -x` to echo each command before it is executed. This is useful for debugging scripts, but it also works for single commands.
```sh
set -x
ls -l
set +x
```
This will print the `ls -l` command before executing it, along with the output.

5. Printing specific parts of the output:
You can use tools like `awk` or `cut` to extract and print specific parts of a command's output.
```sh
echo $(df -h | awk '{print $5}')
```
This will print the percentage of disk space used from `df -h` output.

Important considerations:
- **Quoting:**
    When using command substitution, make sure to use quotes if the output contains spaces or special characters, to avoid unexpected behavior.
- **Error Handling:**
    Command substitution does not automatically capture errors. You may need to redirect stderr for error handling.
- **Nesting:**
    You can nest command substitutions, but be mindful of readability and complexity.