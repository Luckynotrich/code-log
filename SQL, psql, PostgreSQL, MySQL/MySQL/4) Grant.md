### Granting Root-like Privileges

You can create a user that has privileges similar to the default `root` accounts by executing the following:
```sql

CREATE USER 'alexander'@'localhost';
GRANT ALL PRIVILEGES ON  *.* to 'alexander'@'localhost' WITH GRANT OPTION;
```

```sql
show grants for 'lucky'@'localhost';
```
