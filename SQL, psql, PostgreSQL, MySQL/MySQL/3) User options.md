```sql
select user();
```

```sql
CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';
```

```sql
GRANT PRIVILEGE ON database.table TO 'username'@'host';
```

```sql

GRANT CREATE, ALTER, DROP, INSERT, UPDATE, INDEX, DELETE, SELECT, REFERENCES, RELOAD on *.* TO 'sammy'@'localhost' WITH GRANT OPTION;
```

```SQL
GRANT ALL ON greencoast to 'lucky'@'localhost';
```

| Privilege                 | Description                                                                                                                                                                                                                                                                                        |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `CREATE`                  | Create a database using the [CREATE DATABASE](https://mariadb.com/kb/en/create-database/) statement, when the privilege is granted for a database. You can grant the `CREATE` privilege on databases that do not yet exist. This also grants the `CREATE` privilege on all tables in the database. |
| `CREATE ROUTINE`          | Create Stored Programs using the [CREATE PROCEDURE](https://mariadb.com/kb/en/create-procedure/) and [CREATE FUNCTION](https://mariadb.com/kb/en/create-function/) statements.                                                                                                                     |
| `CREATE TEMPORARY TABLES` | Create temporary tables with the [CREATE TEMPORARY TABLE](https://mariadb.com/kb/en/create-table/) statement. This privilege enable writing and dropping those temporary tables                                                                                                                    |
| `DROP`                    | Drop a database using the [DROP DATABASE](https://mariadb.com/kb/en/drop-database/) statement, when the privilege is granted for a database. This also grants the `DROP` privilege on all tables in the database.                                                                                  |
| `EVENT`                   | Create, drop and alter `EVENT`s.                                                                                                                                                                                                                                                                   |
| `GRANT OPTION`            | Grant database privileges. You can only grant privileges that you have.                                                                                                                                                                                                                            |
| `LOCK TABLES`             | Acquire explicit locks using the [LOCK TABLES](https://mariadb.com/kb/en/lock-tables/) statement; you also need to have the `SELECT` privilege on a table, in order to lock it.                                                                                                                    |
| `SHOW CREATE ROUTINE`     | Permit viewing the `SHOW CREATE` definition statement of a routine, for example [SHOW CREATE FUNCTION](https://mariadb.com/kb/en/show-create-function/), even if not the routine owner. From [MariaDB 11.3.0](https://mariadb.com/kb/en/mariadb-11-3-0-release-notes/).                            |