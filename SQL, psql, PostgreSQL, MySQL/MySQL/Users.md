## How to identify locked and password-expired users

The _**mysql.user**_ table stores the user information, including the details about the password expiration states and account lock status. You can query this table as shown below to retrieve the necessary piece of data:

```sql
SELECT 
    User, 
    Host, 
    Account_locked, 
    password_expired 
FROM 
    mysql.user;
```

