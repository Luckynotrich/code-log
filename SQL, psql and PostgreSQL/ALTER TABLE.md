
syntax
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```
example
```sql
ALTER TABLE IF EXISTS table_name
RENAME TO new_table_name;
```

---

## ALTER COLUMN

We want to change the data type of the `year` column of the `cars` table from `INT` to `VARCAHR(4)`.

To modify a column, use the `ALTER COLUMN` statement and the `TYPE` keyword followed by the new data type:

### Example

Change the `year` column from `INT` to `VARCHAR(4)`:

```
ALTER TABLE cars  
ALTER COLUMN year TYPE VARCHAR(4);
```