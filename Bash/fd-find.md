If you use `fd` with no command-line options, it behaves a little like `ls`, except it lists files in sub-directories by default.

```sh
fdfind
```

To see files of a specific type, use the `` `-e` `` (extension) option. Note that you don't have to precede the extension with a period (.), nor is it case sensitive.
```sh
fd -e png
```

To look for a single file, type its name on the command line, like so:
```sh
fd index.html
```

To have the search start in a particular directory, include a file path on the command line. The following command will start a search in the "/etc" directory, and look for files that include `"passwd"` in the file name:

```sh

fdfind passwd /etc
```

Here, we're searching for all C source code files that contain `"coord"` in the file name:

```sh
fdfind -e c coord
```

## fd and Git

Git is an extremely popular [source code version control system](https://git-scm.com/). If you use Git on your computer, you probably use `".gitignore"` files to tell Git which files it should concern itself with, and which it can ignore. By default, `fd` respects the settings in your `".gitignore" `files.

In this directory, we've got a Git repository and `".gitignore"` file. We type the following:

```
ls -adl .git*
```


Let's ask `fd` to list any files that contain "coord" in the file name. We'll then repeat the search and use the `-I` (no ignore) option. This tells `fd` to ignore the settings in the ".gitignore" file and report every matching file.

To do all of this, we type the following:

```
fdfind coord
```

```
fdfind coord -I
```

![[Pasted image 20250129111629.png]]

The two extra files in the second set of results are object files. These are created when a file program is compiled. They're then used by the linker to create the final executable version of the program.

There's an entry in the ".gitignore" file that instructs Git to ignore object files, and, by default, `fd` ignores them, too.

The `-I` (no ignore) option forces `fd` to return everything it finds, rather than being guided by the ".gitginore" file.

## File Types and Case Sensitivity

You can ask `fd` to look for directories, files (including those that are executable and empty), and symbolic links. You can do so by using the `-t` (type) option, followed by one of the letters below:

-   **f**: File.
-   **d**: Directory.
-   **l**: Symbolic link.
-   **x**: Executable file.
-   **e**: Empty file.

The following looks for a directory called images:

```
fdfind -td images
```

## fd versus find: What's the Difference?

The `fd` [command isn't meant to replace](http://manpages.ubuntu.com/manpages/focal/man1/fdfind.1.html) the traditional `find` command, which has [been on Linux, well, forever](http://manpages.ubuntu.com/manpages/focal/man1/find.1.html). Instead, `fd` tries to satisfy the majority of common uses of `find` in a more straightforward way---and, it's often eight or nine times faster than `find`. You can see some of its benchmarks on the project's [GitHub repository page](https://github.com/sharkdp/fd).

`fd` has a colorized output, similar to that of some `ls` modes. It's recursive, but doesn't search hidden directories by default. It knows [about Git](https://git-scm.com/) and will also automatically ignore any patterns in your ".gitignore" file.

`fd` is case insensitive by default. However, if your search pattern contains an uppercase letter, `fd` operates in a case sensitive mode. Of course, you can override the defaults, but, in many cases, they work in your favor.

### Quick Links

- [fd versus find: What's the Difference?](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#fd-versus-find-what-s-the-difference)
    
- [Installing fd](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#installing-fd)
    
- [fd versus fdfind](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#fd-versus-fdfind)
    
- [Simple Searches with fd](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#simple-searches-with-fd)
    
- [fd and Git](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#fd-and-git)
    
- [File Types and Case Sensitivity](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#file-types-and-case-sensitivity)
    
- [Command Execution](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#command-execution)
    
- [Your Go-to Find?](https://www.howtogeek.com/682244/how-to-use-the-fd-command-on-linux/#your-go-to-find)