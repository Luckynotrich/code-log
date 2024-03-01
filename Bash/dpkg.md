## DESCRIPTION         [top](https://man7.org/linux/man-pages/man1/dpkg.1.html#top_of_page)

       **dpkg** is a medium-level tool to install, build, remove and manage
       Debian packages.  The primary and more user-friendly front-end
       for **dpkg** as a CLI (command-line interface) is **apt**(8) and as a TUI
       (terminal user interface) is **aptitude**(8).  **dpkg** itself is
       controlled entirely via command line parameters, which consist of
       exactly one action and zero or more options. The action-parameter
       tells **dpkg** what to do and options control the behavior of the
       action in some way.

       **dpkg** can also be used as a front-end to [dpkg-deb(1)](https://man7.org/linux/man-pages/man1/dpkg-deb.1.html) and
       [dpkg-query(1)](https://man7.org/linux/man-pages/man1/dpkg-query.1.html). The list of supported actions can be found later
       on in the **ACTIONS** section. If any such action is encountered **dpkg**
       just runs **dpkg-deb** or **dpkg-query** with the parameters given to it,
       but no specific options are currently passed to them, to use any
       such option the back-ends need to be called directly.

1. Using:
    
    ```
    sudo dpkg -i /path/to/deb/file
    sudo apt-get install -f
    ```
    
2. Using:
    
    ```
    sudo apt install ./name.deb
    ```
    
    Or
    
    ```
    sudo apt install /path/to/package/name.deb
    ```
    
    With old `apt-get` versions you must first move your deb file to `/var/cache/apt/archives/` directory. For both, after executing this command, it will automatically download its dependencies.
    
3. First installing `gdebi` and then opening your .deb file using it (_Right-click_ -> _Open with_). It will install your .deb package with all its dependencies.
    

**Note**: APT maintains the package index which is a database (`/var/cache/apt/*.bin`) of available packages available in repo defined in `/etc/apt/sources.list` file and in the `/etc/apt/sources.list.d` directory. All these methods will fail to satisfy the software dependency if the dependencies required by the deb is not present in the package index.
---

### Why use `sudo apt-get install -f` after `sudo dpkg -i /path/to/deb/file` (as mentioned in method 1)?

From `man apt-get`:

```
 -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
```

When `dpkg` installs a package and a package dependency is not satisfied, it leaves the package in an "unconfigured" state and that package is considered broken.

The `sudo apt-get install -f` command tries to fix this broken package by installing the missing dependency.