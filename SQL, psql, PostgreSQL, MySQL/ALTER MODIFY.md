
##### change column position
```sql
ALTER TABLE event MODIFY COLUMN end_time TIME  AFTER start_time;
```

#####  Change the length of a `varchar` column
```SQL
ALTER TABLE t3 MODIFY COLUMN alcol1 VARCHAR(6);
```
