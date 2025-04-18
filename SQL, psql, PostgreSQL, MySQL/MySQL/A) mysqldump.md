**Dump table single data**
```sh
mysqldump -u lucky -p greencoast user > gtc_user_bu.sql
```

**Restore data**
First log in to `mysql` shell command line,
then
```sql
source gtc_user_bu.sql
```
