pack
```
tar -czvf dist.tar.gz dist/
```

list
```sh
tar -tvf dist.tar
```
unpack
```
rm -rf dist/
tar -xvf dist.tar.gz dist/
```

exclude
```sh
tar -X 'tar-exclude.txt' -czvf greencoast.tar.gz . # This line may not work

```

To compress using **bzip2** compression
```sh
$ tar -cjvf sales.tar.bz2 sales1.pdf sales2.pdf sales3.pdf
```

list
```sh
tar -jtvf archive.tar.bz2
```

To decompress a ‘`.tar.bz2`’ file 
```sh
tar -jxvf archive.tar.bz2

```

**exclude**
```sh
# This command worked from the parent directory 
tar --exclude="./rhbackend/node_modules/*" --exclude="./rhbackend/richardhaskell/.git/*" -jcvf richardhaskell.tar.bz2 ./rhbackend index.html;

```

