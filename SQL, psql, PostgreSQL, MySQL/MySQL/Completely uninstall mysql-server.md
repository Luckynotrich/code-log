_**Warning:** This solution will delete all your data stored on the MySQL server!_

```
sudo apt remove --purge mysql-server
sudo apt purge mysql-server
sudo apt autoremove
sudo apt autoclean
sudo apt remove dbconfig-mysql
```

Install MySQL:

```
sudo apt install mysql-server
```

After installing the server, doing `sudo mysql` should open MySQL