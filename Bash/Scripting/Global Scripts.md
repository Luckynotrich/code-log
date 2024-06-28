# [Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)

[Wikipedia](https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

A common place to make scripts accessible to anyone with root privileges -  `/usr/local/bin/` 
File extensions don't matter to the system.

```
sudo mv update.sh /usr/local/bin/update
```

```
	sudo chown root:root /usr/local/bin/update
```

```
which update
```

```
echo $PATH
/home/lucky/.nvm/versions/node/v20.9.0/bin:/home/lucky/.local/bin:/home/lucky/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin:/home/lucky/.dotnet/tools:/home/lucky/.local/bin

```

