 ta[`commandprompt.com`](https://www.commandprompt.com/education/postgresql-delete-cascade-with-examples/)

In PostgreSQL, a **DELETE CASCADE** is a powerful feature that is useful when you have multiple tables linked with each other via foreign key constraints. When a DELETE CASCADE feature is enabled, deleting a record from the referenced/parent table will also delete the referencing records from the child table.

To use a delete cascade in Postgres, specify the "**ON DELETE CASCADE**" option while creating/defining a foreign key constraint. This tells Postgres to automatically delete any rows in the referenced table that are related to the row being deleted in the referencing table.

#### [Tech on the Net: SQL Server: Foreign Keys with cascade delete](https://www.techonthenet.com/sql_server/foreign_keys/foreign_delete.php)

