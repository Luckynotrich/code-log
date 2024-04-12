## [PostgreSQL copy database within the same server](https://www.postgresqltutorial.com/postgresql-administration/postgresql-copy-database/)

Sometimes, you want to copy a PostgreSQL database within a database server for testing purposes.

PostgreSQL makes it easy to do so via the [`CREATE DATABASE`](https://www.postgrepgsqltutorial.com/postgrepgsql-create-database/) statement, as follows:

```
CREATE DATABASE targetdb  WITH TEMPLATE sourcedb;`
Code language: PostgreSQL SQL dialect and PL/pgSQL (pgsql)
```

This statement copies the `sourcedb` to the `targetdb`. For example, to copy the `dvdrental` [sample database](https://www.postgrepgsqltutorial.com/postgrepgsql-sample-database/) to the `dvdrental_test` database, you use the following statement:

```
CREATE DATABASE dvdrental_test  WITH TEMPLATE dvdrental;
```

