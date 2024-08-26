## Example

For example, if you had an entry with User and Host column values of '`bob`' and '`%.loc.gov`', you would write the statement like this:
```sql

SET PASSWORD FOR 'bob'@'%.loc.gov' = PASSWORD('newpass');
```
If you want to delete a password for a user, you would do:
```sql
SET PASSWORD FOR 'bob'@localhost = PASSWORD("");
```