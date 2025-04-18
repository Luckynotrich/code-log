	#### change column **name**
```sql
ALTER TABLE event RENAME COLUMN loc_name TO event_name;
```

#### change **position** in table:
```sql
ALTER TABLE _event CHANGE COLUMN type type varchar(50) AFTER event_id;
```

#### change column **type**
```sql
ALTER TABLE _event CHANGE COLUMN event_type event_type VARCHAR(15);
```

**Using SQL Query:**

Columns are `nullable` by default, so for an existing column with `NOT NULL` defined, you just have to modify it, put in the same data type but remove the `NOT NULL` part:

```sql

ALTER TABLE table_name MODIFY col_name data_type;
```

Or use `CHANGE`:

```sql

ALTER TABLE table_name CHANGE col_name col_name data_type DEFAULT NULL;
```

`DEFAULT NULL` is optional.

