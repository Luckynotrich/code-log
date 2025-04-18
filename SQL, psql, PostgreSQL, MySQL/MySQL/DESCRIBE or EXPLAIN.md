```sql
DESCRIBE user;
```

![[Pasted image 20250205134735.png]]

[EXPLAIN ](https://dev.mysql.com/doc/refman/8.4/en/explain.html) is a synonym  for DESCRIBE


```SQL
explainable_stmt: {
    SELECT statement
  | TABLE statement
  | DELETE statement
  | INSERT statement
  | REPLACE statement
  | UPDATE statement
}
```