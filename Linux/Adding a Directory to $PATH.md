## [Step 1 — Viewing the `PATH` Variable](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-1-mdash-viewing-the-path-variable)

You can view the `PATH` variable with the following command:
```sh
echo $PATH
```

Some directories are mentioned by default, and each directory in `PATH` is separated with a colon `:`. The system checks these directories from left to right when running a program.

When a command-line program is not installed in any of the mentioned directories, you may need to add the directory of that program to `PATH`.

### [Step 2 — Adding a Directory to the `PATH` Environment Variable](https://www.digitalocean.com/community/tutorials/how-to-view-and-update-the-linux-path-environment-variable#step-2-mdash-adding-a-directory-to-the-path-environment-variable)

A directory can be added **temporarily** to `PATH` in two ways: at the start or the end of a path.

Adding a directory (`/the/file/path` for example) to the start of `PATH` will mean it is checked first:
```sh
export PATH=/the/file/path:$PATH
```

Adding a directory to the end of `PATH` means it will be checked after all other directories:
```sh
export PATH=$PATH:/the/file/path

```

Multiple directories can be added to `PATH` at once by adding a colon `:` between the directories:
```sh
export PATH=$PATH:/the/file/path:/the/file/path2
```

### These methods will only work for the current shell session.
Once you exit the current session and start a new one, the `PATH` variable will reset to its default value and no longer contain the directory you added. For the `PATH` to persist across different shell sessions, it has to be stored in a file.

### Step 3 — Permanently Adding a Directory to the PATH Variable

In this step, you will add a directory permanently in the shell configuration file, which is `~/.bashrc` if you’re using a bash shell or `~/.zshrc` if you’re using a `zsh` shell. This tutorial will use `~/.bashrc` as an example.

First, open the `~/.bashrc` file:
```sh
nano ~/.bashrc
```

The `~/.bashrc` file will have existing data, which you will not modify. At the bottom of the file, add the `export` command with your new directory:
```sh
...
Adding paths to your PATH
export PATH=$PATH:the/file/path
```

Use the methods described in the prior section to clarify whether you want the new directory to be checked first or last in the `PATH`.

Save and close the file. The changes to the `PATH` variable will be made once a new shell session is started. To apply the changes to the current session, use the `source` command:
```sh
source ~/.bashrc
```

The `PATH` environment variable is a crucial aspect of command-line use. It enables you to run command-line programs, such as `echo` and `python3`, from any directory without typing the full path.

**WARNING: The scripts pip, `pip3` and `pip3.10` are installed in '/home/lucky/.local/bin' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.**