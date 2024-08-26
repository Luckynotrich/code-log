We can check whether a file exists using the [`test`](https://en.wikipedia.org/wiki/Test_(Unix)) command-line utility:

Click to Copy

`if test -f /path/to/file; then   echo "File exists." fi`

To check whether a file does not exist, we can negate the condition with the NOT logical operator, `!`:

Click to Copy

`if ! test -f /path/to/file; then   echo "File does not exist." fi`

Because the `test` command is used frequently in Bash expressions, we can write it as `[]` rather than typing out `test`:

Click to Copy

`if ! [ -f /path/to/file ]; then   echo "File does not exist." fi`

The `-f` flag tests whether the provided filename exists and is a regular file. To test for directories instead, we can use the `-d` flag. To test for both files and directories, we can use the `-e` flag.

More information about `test` can be found on its manual page, accessible by typing `man test` into the terminal.