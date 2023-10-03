## What is the find command in Linux?

The `find` command lets you efficiently search for files, folders, and character and block devices.

Below is the basic syntax of the `find` command:

```bash
find /path/ -type f -name file-to-search
```

Where,

-   `/path` is the path where file is expected to be found. This is the starting point to search files. The path can also be`/`or `.` which represent root and current directory, respectively.
-   `-type` represents the file descriptors. They can be any of the below:

`f` – **Regular file** such as text files, images and hidden files.

`d` – **Directory**. These are the folders under consideration.

`l` – **Symbolic link**. Symbolic links point to files and are similar to shortcuts.

`c` – **Character devices**. Files that are used to access character devices are called character device files. Drivers communicate with character devices by sending and receiving single characters (bytes, octets).  Examples include     keyboards, sound cards and mouse.

`b` – **Block devices**. Files that are used to access block devices are called block device files. Drivers communicate with block devices by sending and receiving entire blocks of data. Examples include USB, CD-ROM

-   `-name` is the name of the file type that you want to search.