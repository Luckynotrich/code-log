# [PostgreSQL UPDATE](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-update/)

The PostgreSQL UPDATE statement allows you to update data in one or more columns of one or more rows in a table.

Here’s the basic syntax of the UPDATE statement:

```SQL
UPDATE table_name
SET column1 = value1,
    column2 = value2,
    ...
WHERE condition;
RETURNING * | output_expression AS output_name;
```

example:
```sql
update public.user set password = '$2b$10$jf6aIIpO974uC9hMzQtGC.wGD0In49aLcwdDhSoI0IV2WX/vKxC6q'
where user_name = 'luckyman';
```