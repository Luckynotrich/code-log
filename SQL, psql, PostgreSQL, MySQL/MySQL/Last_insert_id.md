You can use [LAST_INSERT_ID()](https://dev.mysql.com/doc/refman/5.7/en/information-functions.html#function_last-insert-id).

Quoted from docs:

**LAST_INSERT_ID(), LAST_INSERT_ID(expr)**

> With no argument, `LAST_INSERT_ID()` returns a `BIGINT UNSIGNED` (64-bit) value representing the first automatically generated value successfully inserted for an `AUTO_INCREMENT` column as a result of **the most recently executed `INSERT` statement**. The value of `LAST_INSERT_ID()` remains unchanged if no rows are successfully inserted.
> 
> With an argument, `LAST_INSERT_ID()` returns an unsigned integer.
> 
> ```sql
> SELECT LAST_INSERT_ID();
> ```

You can find an extended example in this chapter:

[28.7.29.3 How to Get the Unique ID for the Last Inserted Row](https://dev.mysql.com/doc/refman/8.0/en/getting-unique-id.html)

```sql
CREATE TABLE T
(
    ID INT AUTO_INCREMENT PRIMARY KEY,
    FOO INT
);

INSERT INTO T (FOO) VALUES (100);
INSERT INTO T (FOO) VALUES (200);
INSERT INTO T (FOO) VALUES (300);

SELECT * FROM T WHERE ID = LAST_INSERT_ID();

ID | FOO
-: | --:
 3 | 300
```

Let me add the advice [Akina](https://dba.stackexchange.com/users/150107/akina) has pointed out in comments:

> There is a problem. LAST_INSERT_ID() scope is connection. If connection pool used or re-connection occurred, zero will be returned. One of the solutions is to execute all queries within stored procedure.

In case you don't delete any of the rows in your table, this should work :

```sql
SELECT * FROM Food WHERE id = (SELECT MAX(id) FROM Food) ;
```

