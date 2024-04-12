`\du`  - display user
`\l` - list databases
`\? ` - list commands
`\q` - quit psql
`\c db_name` - connect to other database

execute SQL file
```
sql\i /root/test.sql
```

If you wish to execute the script right from the database host terminal without first logging in to Postgres, you can do so with **`-f`** option. For example:

```plain
psql -U your_username -d your_database_name -f /path/to/script.sql
```
