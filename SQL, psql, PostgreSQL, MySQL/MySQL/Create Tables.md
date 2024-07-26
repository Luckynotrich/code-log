```sql
CREATE TABLE employees (
	employee_id INT,
	first_name VARCHAR(50),
	last_name VARCHAR(50),
	hourly_pay DECIMAL(5,2),-- max value $999.99
	hire_date DATE
);
```

To rename table:
```sql
RENAME TABLE employees TO  workers;
```

To drop table:
```sql
DROP TABLE employees;
```

To add a Column:
```sql
ALTER TABLE employees ADD phone_number VARCHAR(15);
```

Rename Column:
```sql
ALTER TABLE employees RENAME COLUMN phone_number TO  email;
```

Modify Column:
```sql
ALTER TABLE employees MODIFY COLUMN email VARCHAR(100);
```

Move Column:
```sql
ALTER TABLE employees MODIFY email VARCHAR(100) AFTER LAST_NAME;
```

Drop Column:
```sql
ALTER TABLE employees DROP COLUMN email;
```