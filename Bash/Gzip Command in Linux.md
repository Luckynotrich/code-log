# [Gzip Command in Linux](https://linuxize.com/post/gzip-command-in-linux/)
## Compressing Files with `gzip`

To compress a single file, invoke the `gzip` command followed by the filename:

```
gzip filename
```

`gzip` will create a file `filename.gz` and delete the original file.

By default, `gzip` keeps the original file timestamp, mode, ownership, and name in the compressed file.

### Keep the original file

If you want to keep the input (original) file, use the `-k` option:

```
gzip -k filename
```

Another option to keep the original file is to use the `-c` option, which tells `gzip` to write on standard output and redirect the output to a file:

```
gzip -c filename > filename.gz
```

### Verbose output

Use the `-v` option if you want to see the percentage reduction and the names of the files that are being processed:

```
gzip -v filename   
```

```output
filename:	  7.5% -- replaced with filename.gz
```

### Compress multiple files

You can also pass multiple files as arguments to the command. For example, to compress the files named `file1`, `file2`, `file3`, you would run the following command:

```
gzip file1 file2 file3
```

The command above will create three compressed files, `file1.gz`, `file2.gz`, `file3.gz`.

### Compress all files in a directory

To compress all files in a given directory recursively, use the `-r` option:

```
gzip -r directory
```

`gzip` will recursively traverse through the whole directory structure and compress all the files in the directory and it’s sub-directories.

The above utility is not recommended to use, otherwise it can create complications while recovering the data.
### Change the compression level

`gzip` allows you to specify a range of compression levels, from 1 to 9. `-1` or `--fast` means the fastest compression speed with minimal compression ratio, and `-9` or `--best` indicates the slowest compression speed with maximum compression ratio. The default compression level is `-6`.

For example, to get maximum compression, you would run:

```
gzip -9 filename
```

Compression is a CPU-intensive task; the higher the compression level, the longer the process takes.

### Using standard input

To create a `.gz` file from the stdin, pipe the output of the command to `gzip`. For example, to create a Gzipped [MySQL database backup](https://linuxize.com/post/how-to-back-up-and-restore-mysql-databases-with-mysqldump/) , you would run:

```
mysqldump database_name | gzip -c > database_name.sql.gz
```

The output of the `mysqldump` command will be input for `gzip`.

## Decompressing Files with `gzip`

To [decompress a `.gz` file](https://linuxize.com/post/how-to-unzip-gz-file/) , use the `-d` option:

```
gzip -d filename.gz
```

Another command that you can use to decompress a Gzip file is [`gunzip`](https://linuxize.com/post/gunzip-command-in-linux/) . This command is just an alias to `gzip -d`:

```
gunzip filename.gz
```

You might find it easier to remember `gunzip` than `gzip -d`.

### Keep the compressed file

Same as when compressing a file, the `-k` option tells `gzip` to keep the input file, in this case, that is the compressed file:

```
gzip -dk filename.gz
```

### Decompress multiple files

To decompress multiple files at once, pass the filenames to the `gzip` command as arguments:

```
gzip -d file1.gz file2.gz file3.gz
```

### Decompress all files in a directory

When used with `-d` and `-r` options, `gzip` decompresses all files in a given directory recursively:

```
gzip -dr directory
```

## List the Compressed File Contents

When used with the `-l` option, the `gzip` command shows statistics about the given compressed files:

```
gzip -l filename
```

The output will include the uncompressed file name, the compressed and uncompressed size, and the compression ratio:

```output
         compressed        uncompressed  ratio uncompressed_name
                130                 107   7.5% filename
```

To get more information, add the `-v` option:

```
gzip -lv filename
```

```output
method  crc     date  time           compressed        uncompressed  ratio uncompressed_name
defla a9b9e776 Sep  3 21:20                 130                 107   7.5% filename
```

## Conclusion

With Gzip, you can reduce the size of a given file. The `gzip` command allows you to compress and decompress files.

For more information about the `gzip` command, consult the [Gnu gzip documentation page](https://www.gnu.org/software/gzip/manual/gzip.html) .

If you have any questions, please leave a comment below.

[gzip](https://linuxize.com/tags/gzip/) [terminal](https://linuxize.com/tags/terminal/)

Related Tutorials

- [Gunzip Command in Linux](https://linuxize.com/post/gunzip-command-in-linux/)
- [How to Extract (Unzip) Tar Gz File](https://linuxize.com/post/how-to-extract-unzip-tar-gz-file/)
- [How to Unzip (Extract) Gz File in Linux](https://linuxize.com/post/how-to-unzip-gz-file/)
- [Understanding the /etc/shadow File](https://linuxize.com/post/etc-shadow-file/)
- [Basic Linux Commands](https://linuxize.com/post/basic-linux-commands/)
- [Bash: Append to File](https://linuxize.com/post/bash-append-to-file/)
- [How to Recursively Change the File's Permissions in Linux](https://linuxize.com/post/chmod-recursive/)
- 