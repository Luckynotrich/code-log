Listing system variables
```sh
sudo mysqld --verbos --help
```

By default, MySQL stores database files in **/var/lib/mysql**. However, we can override the location in the configuration file. Typically, this is the `/etc/mysql/mysql. conf` - [

[Where Does MySQL Store Its Database Files? - Baeldung](https://www.google.com/url?sa=t&source=web&rct=j&opi=89978449&url=https://www.baeldung.com/linux/mysql-database-files-location&ved=2ahUKEwi5t_rk2ZOIAxXwADQIHVZgN6cQFnoECBcQAw&usg=AOvVaw0mcJryrrFz_O2H5u61UhyH)

[MySQL 8.4 Reference Manual](https://dev.mysql.com/doc/refman/8.4/en/)  /
[Using System Variables](https://dev.mysql.com/doc/refman/8.4/en/using-system-variables.html)  

7.1.9 Using System Variables
- Set a global system variable:
    
    ```sql
    SET GLOBAL max_connections = 1000;
    SET @@GLOBAL.max_connections = 1000;
    ```
    
- Persist a global system variable to the `mysqld-auto.cnf` file (and set the runtime value):
    
    ```sql
    SET PERSIST max_connections = 1000;
    SET @@PERSIST.max_connections = 1000;
    ```
    
- Persist a global system variable to the `mysqld-auto.cnf` file (without setting the runtime value):
    
    ```sql
    SET PERSIST_ONLY back_log = 1000;
    SET @@PERSIST_ONLY.back_log = 1000;
    ```
    
- Set a session system variable:
    
    `SET SESSION sql_mode = 'TRADITIONAL'; SET @@SESSION.sql_mode = 'TRADITIONAL'; SET @@sql_mode = 'TRADITIONAL';`


