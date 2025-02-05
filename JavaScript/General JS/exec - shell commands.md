#### [ `child_process.exec(command[, options][, callback])`](https://nodejs.org/api/child_process.html#child_processexeccommand-options-callback)

Spawns a shell then executes the `command` within that shell, buffering any generated output. The `command` string passed to the exec function is processed directly by the shell and special characters (vary based on [shell](https://en.wikipedia.org/wiki/List_of_command-line_interpreters)) need to be dealt with accordingly:
```js
const { exec } = require('node:child_process');

exec('"/path/to/test file/test.sh" arg1 arg2');
// Double quotes are used so that the space in the path is not interpreted as
// a delimiter of multiple arguments.

exec('echo "The \\$HOME variable is $HOME"');
// The $HOME variable is escaped in the first instance, but not in the second.
```

**Never pass non-sanitized user input to this function. Any input containing shell meta characters may be used to trigger arbitrary command execution.**

If a `callback` function is provided, it is called with the arguments `(error, stdout, stderr)`. On success, `error` will be `null`. On error, `error` will be an instance of [`Error`](https://nodejs.org/api/errors.html#class-error). The `error.code` property will be the exit code of the process. By convention, any exit code other than `0` indicates an error. `error.signal` will be the signal that terminated the process.

The `stdout` and `stderr` arguments passed to the callback will contain the `stdout` and `stderr` output of the child process. By default, Node.js will decode the output as `UTF-8` and pass strings to the callback. The encoding option can be used to specify the character encoding used to decode the `stdout` and `stderr` output. If encoding is 'buffer', or an unrecognized character encoding, Buffer objects will be passed to the callback instead.
```JS
const { exec } = require('node:child_process');
exec('cat *.js missing_file | wc -l', (error, stdout, stderr) => {
  if (error) {
    console.error(`exec error: ${error}`);
    return;
  }
  console.log(``stdout`: ${stdout}`);
  console.error(`stderr: ${stderr}`);
});
```