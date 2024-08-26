## Testing for a file

It's common to want to know whether a file exists, often so you can confidently proceed with some action, or so you can avoid "clobbering" it with a file of the same name. In an interactive shell session, you can just look to see whether the file exists but in a shell script, you need the computer to determine that for itself. The `-e` option tests whether a file exists, but its apparent response is the same either way.

```bash
$ touch example
$ test -e example
$ test -e notafile
$
```

The `[` and `test` commands are essentially switches. They emit a `true` or `false` response, but considers both of them as success. You can put this to use by pairing the commands with logical operators, such as `&&` and `||`. The `&&` operator is executed when a response is `true`:

```bash
$ touch example
$ test -e example && echo "foo"
foo
$ test -e notafile && echo "foo"
$
```

The `||` operator executes when a response is `false`:

```bash
$ touch example
$ test -e example || echo "foo"
$ test -e notafile || echo "foo"
foo
$
```

If you prefer, you can use square brackets instead of `test`. In all cases, the results are the same:

```bash
$ touch example
$ [ -e example &#93; && echo "foo"
foo
$ [ -e notafile &#93; && echo "foo"
$
```

## Testing for file types

Everything in Linux is a file, so when you can test for the existence of a directory with the `-e` option, the same way you test for a file. However, there are different kinds of files, and sometimes that matters. You can use `[` or `test` to detect a variety of different file types:

- `-f`: regular file (returns `false` for a directory)
    
- `-d`: directory
    
- `-b`: block (such as `/dev/sda1`)
    
- `-L` or `-h`: symlink
    
- `-S`: socket
    

There are more, but those tend to be the most common.

## Testing for file attributes

You can also look at metadata of a file:

- `-s`: a file with the size greater than zero
    
- `-N`: a file that's been modified since it was last read
    

You can test by ownership:

- `-O`: a file owned by the current primary user
    
- `-G`: a file owned by the current primary group
    

Or you can test by permissions (or _file mode_):

- `-r`: a file with read permission granted
    
- `-w`: a file with write permission granted
    
- `-x`: a file with execute permission granted
    
- `-k`: a file with the sticky bit set
    

## Combining tests

You don't always just have to test for a single attribute. The `-a` option ("and") allows you to string several tests together, with the requirement that all tests return as `true`:

```bash
$ touch zombie apocalypse now
$ test -e zombie -a -e apocalypse -a -e now && echo "no thanks"
no thanks
```

If any expression fails, then the test returns `false`:

```bash
$ touch zombie apocalypse now
$ test -e plant -a -e apocalypse -a -e now && echo "no thanks"
$
```

The `-o` option ("or") requires that one expression is true:

```bash
$ touch zombie apocalypse now
$ test -e zombie -o -e plant -o -e apocalypse && echo "no thanks"
no thanks
```