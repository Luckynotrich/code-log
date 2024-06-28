## Syntax of the tar command

The **tar** command accepts the following syntax −

```
tar [options][archive-file] [file or dir to be archived]
```

Let's look at some of the options provided with the **tar** command.
### tar command options

The **tar** command provides the following options −
     _-c_ − This creates an archive file.
     _-x_ − The option extracts the archive file.
    _-f_ − Specifies the filename of the archive file.
    _-v_ - This prints verbose information for any tar operation on the terminal.
    _-t_ − This lists all the files inside an archive file.
    _-u_ − This archives a file and then adds it to an existing archive file.
    _-r_ − This updates a file or directory located inside a .tar file
    _-z_ − Creates a tar file using gzip compression
    _-j_ − Create an archive file using the bzip2 compression
    _-W_ − The -w option verifies an archive file.
    
## Creating an archive file

The **tar** utility allows you to create archive files using various compression algorithms such as **xz**, **gzip** and **bzip2**. The accepted convention is to add the compression suffix to the compressed file.

For example, when using **gzip** compression (using the “-z” option), the file must have the suffix “`.tar.gz`”.

```
$ tar -czvf sales.tar.gz  sales1.pdf sales2.pdf sales3.pdf
```

In this example, the command creates a file named “`sales.tar.gz`” from the three PDF files.

Similarly, when using **bzip2** compression (using the “-j” option), the archive file must have the extension “`.tar.bz2`” as a suffix.

```
$ tar -cjvf sales.tar.bz2 sales1.pdf sales2.pdf sales3.pdf
```

*Besides archiving files, you can also compress directories.* For example, the following command creates a simple home directory tarball.

`$ tar -cvf home.tar /home/james`

### List the contents of an archive file

The “-t” option can be used to list the contents of an archive file without extracting it.

`$ tar -tf sales.tar.gz`

This command lists all files within the “`sales.tar.gz`” archive.

## Extracting an archive file

There are several ways to extract a compressed file using the **tar** command.

### Extract to current directory

To extract an archive into the current working directory, use the “-x” option as shown below.

`$ tar -xvf documents.tar.gz`

In this example, we are unzipping or extracting the “`documents.tar.gz`” file, which contains three text files.

### Extraction in separate directory

To extract an archive to a different directory, the ‘-C’ option is followed by the destination path, as shown in the following example.

`$ tar -xvf documents.tar.gz -C /tmp/files`

This command extracts the contents of the “`documents.tar.gz`” archive file into the `/tmp/files` directory.

### Extract specific files from an archive

You can extract certain specified files by listing them one by one on the command line.

`$ tar -xvf documents.tar.gz file1.txt file2.txt`

In this example, we are extracting the files “`file1.txt`” and “`file2.txt`” from the “`documents.tar.gz`” archive.

## Adding a File to a .tar Archive

To add or append a ‘.tar’ archive file, use the ‘-r’ option as shown.

`$ tar -rvf files.tar file3.txt`

In this example, we are adding the `file3.txt` file to the archives.tar file.

## Deleting a file from a .tar file

To remove a file from a ‘.tar’ archive, use the **--delete** option as shown.

$ `tar --delete -f archives.tar file3.txt`

In this example, we are removing the “`file3.txt`” file from the archives.tar file.

The syntax to remove a directory from a tar ball is as follows:

`tar --delete -f file.tar 'path1/dir1'`

OR

`tar --delete -f file.tar 'dir1'`

To delete a directory called etc/security from a foo.tar, enter:  
`$ tar --delete -f foo.tar 'etc/security'`  
Verify that directory has been deleted from the foo.tar ball, enter:  
`$ tar -tvf foo.tar | less`  
OR  
`$ tar -tvf foo.tar | grep 'etc/security'`
### Compress an archive

The tar command can also be used to compress an archive using **gzip or bzip2 compression**. To create a compressed file, the **-z** or **-j** option can be used in conjunction with the -c option.

`$ tar -zcvf archive.tar.gz files_to_compress`

This command creates a “`.tar.gz`” archive of the specified files.

`$ tar -jcvf archive.tar.bz2 files_to_compress`

This command creates a “`.tar.bz2`” archive of the specified files.

### unzip a archive

To decompress a ‘`.tar.gz`’ file −

`$ tar -zxvf archive.tar.gz`

To decompress a ‘`.tar.bz2`’ file −

`$ tar -jxvf archive.tar.bz2`