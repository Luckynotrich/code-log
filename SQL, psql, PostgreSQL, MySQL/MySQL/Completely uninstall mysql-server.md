_**Warning:** This solution will delete all your data stored on the MySQL server!_

```
sudo apt purge mysql*
sudo apt autoremove

sudo rm -rf /etc/mysql
sudo rm -rf /var/lib/mysql
```

Install MySQL:

```
sudo apt install mysql-server
```

After installing the server, doing `sudo mysql` should open MySQL