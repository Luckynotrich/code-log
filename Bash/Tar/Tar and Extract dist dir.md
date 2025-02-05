pack
```
tar -czvf dist.tar.gz dist/
```

unpack
```
rm -rf dist/
tar -xvf dist.tar.gz dist/
```

```sh
tar -X 'tar-exclude.txt' -czvf greencoast.tar.gz .
```

To compress using **bzip2** compression
```sh
$ tar -cjvf sales.tar.bz2 sales1.pdf sales2.pdf sales3.pdf
```

To decompress a ‘`.tar.bz2`’ file 
```sh
tar -jxvf archive.tar.bz2
```