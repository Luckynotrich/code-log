```sql
ALTER TABLE Persons  
ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
```

```sql
alter table _event add column event_type varchar(30) after event_name;
```