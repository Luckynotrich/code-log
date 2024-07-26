change column name
```sql
ALTER TABLE event RENAME COLUMN loc_name TO event_name;
```

change position in table:
```sql
ALTER TABLE event CHANGE COLUMN type type varchar(50) AFTER event_id;
```

change column type
```sql
ALTER TABLE event CHANGE COLUMN event_type event_type VARCHAR(15);
```