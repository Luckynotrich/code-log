[Create Users Table ](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=392s)
```sql
	CREATE TABLE users(
	id BIGSERIAL PRIMARY KEY,
	name VARCHAR(20) NOT NULL,
	email VARCHAR(200) NOT NULL,
	password VARCHAR(200) NOT NULL
);
```