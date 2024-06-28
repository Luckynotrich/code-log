### Miscellaneous operators

These miscellaneous operators show whether a shell option is set or a shell variable has a value, but it does not discover the value of the variable, just whether it has one.

| Operator   | Description                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -o optname | True if the shell option optname is enabled (see the list of options under the description of the **-o** option to the Bash set builtin in the Bash man page) |
| -v varname | True if the shell variable varname is set (has been assigned a value)                                                                                         |
| -R varname | True if the shell variable varname is set and is a name reference                                                                                             |