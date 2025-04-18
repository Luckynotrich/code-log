```sql
INSERT INTO _table_name_ (_column1_, _column2_, _column3_, ...)   
VALUES (_value1_, _value2_, _value3_, ...);
```

```js
const result = await pool.query('INSERT INTO user (user_name, user_roles, password) VALUES (?,?,?)', [user, roles, hashedPwd]);
```

