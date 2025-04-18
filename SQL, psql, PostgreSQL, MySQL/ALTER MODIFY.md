
##### change column position
```sql
ALTER TABLE event MODIFY COLUMN end_time TIME  AFTER start_time;
```

#####  Change the size of a `varchar` column
```SQL
ALTER TABLE _event MODIFY COLUMN teaser VARCHAR(700);
```
