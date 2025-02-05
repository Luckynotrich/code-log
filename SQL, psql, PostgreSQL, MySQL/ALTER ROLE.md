[ How to Change the Password of a PostgreSQL User](https://www.postgresqltutorial.com/postgresql-administration/postgresql-change-password/)
```
ALTER ROLE username   
WITH PASSWORD 'password';
```

For MySQL version 5.7.6 or later, use 
```sql
ALTER USER 'username'@'localhost' IDENTIFIED BY 'new_password'
	       ^        ^ ^         ^
```