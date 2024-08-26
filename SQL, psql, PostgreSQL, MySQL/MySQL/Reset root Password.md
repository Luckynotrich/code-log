# Restart the service without authentication

## Ubuntu/Debian

```
service mysql stop
service mysql start --skip-grant-tables --skip-networking
```

## Other sysv

If you're on a `sysv` Linux use this

```
/etc/init.d/mysqld stop
/etc/init.d/mysqld start --skip-grant-tables --skip-networking &
```

# Resetting

Then you need to login as `root`

```
mysql -u root -p
```

Then when logged in run

```
FLUSH PRIVILEGES;
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPass';
```
