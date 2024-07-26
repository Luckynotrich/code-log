```sql
CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';
```

```sql
GRANT PRIVILEGE ON database.table TO 'username'@'host';
```

```sql

GRANT CREATE, ALTER, DROP, INSERT, UPDATE, INDEX, DELETE, SELECT, REFERENCES, RELOAD on *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```
