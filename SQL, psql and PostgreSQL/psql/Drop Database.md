# [PostgreSQL DROP DATABASE](https://www.postgresqltutorial.com/postgresql-administration/postgresql-drop-database/)


**Summary**: in this tutorial, you will learn how to use the PostgreSQL `DROP DATABASE` statement to drop a database.

## Introduction to PostgreSQL DROP DATABASE statement

The `DROP DATABASE` statement deletes a database from a PostgreSQL server.

Here’s the basic syntax of the `DROP DATABASE` statement:

```sql
DROP DATABASE [IF EXISTS] database_name
[WITH (FORCE)];
```


Example:
```
DROP DATABASE test WITH (FORCE);
```