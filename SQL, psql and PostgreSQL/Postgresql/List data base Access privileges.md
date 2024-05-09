`\l richar65_future_self2`

```
richar65_future_self2=> \l richar65_future_self2
                                                           List of databases
         Name          |         Owner         | Encoding |   Collate   |    Ctype    |                                
-----------------------+-----------------------+----------+-------------+-------------+---------------------

 richar65_future_self2 | richar65_future_self2 | UTF8     | en_US.UTF-8 | en_US.UTF-8 | 
                       |                       |          |             |             | 

Access privileges
---------------------------- 
 =Tc/richar65_future_self2                      +
richar65_future_self2=CTc/richar65_future_self2
(1 row)

```
Table above say `richar65_future_self2 has Tc and CTc`

**Table 5.1. [ACL Privilege Abbreviations](https://www.postgresql.org/docs/12/ddl-priv.html#PRIVILEGE-ABBREVS-TABLE)**

  
|Privilege|Abbreviation|Applicable Object Types|
|---|---|---|
|`SELECT`|`r` (“read”)|`LARGE OBJECT`, `SEQUENCE`, `TABLE` (and table-like objects), table column|
|`INSERT`|`a` (“append”)|`TABLE`, table column|
|`UPDATE`|`w` (“write”)|`LARGE OBJECT`, `SEQUENCE`, `TABLE`, table column|
|`DELETE`|`d`|`TABLE`|
|`TRUNCATE`|`D`|`TABLE`|
|`REFERENCES`|`x`|`TABLE`, table column|
|`TRIGGER`|`t`|`TABLE`|
|`CREATE`|`C`|`DATABASE`, `SCHEMA`, `TABLESPACE`|
|`CONNECT`|`c`|`DATABASE`|
|`TEMPORARY`|`T`|`DATABASE`|
|`EXECUTE`|`X`|`FUNCTION`, `PROCEDURE`|
|`USAGE`|`U`|`DOMAIN`, `FOREIGN DATA WRAPPER`, `FOREIGN SERVER`, `LANGUAGE`, `SCHEMA`, `SEQUENCE`, `TYPE`|

[Table 5.2](https://www.postgresql.org/docs/12/ddl-priv.html#PRIVILEGES-SUMMARY-TABLE "Table 5.2. Summary of Access Privileges") summarizes the privileges available for each type of SQL object, using the abbreviations shown above. It also shows the psql command that can be used to examine privilege settings for each object type.

**Table 5.2. Summary of Access Privileges**

   
|Object Type|All Privileges|Default `PUBLIC` Privileges|psql Command|
|---|---|---|---|
|`DATABASE`|`CTc`|`Tc`|`\l`|
|`DOMAIN`|`U`|`U`|`\dD+`|
|`FUNCTION` or `PROCEDURE`|`X`|`X`|`\df+`|
|`FOREIGN DATA WRAPPER`|`U`|none|`\dew+`|
|`FOREIGN SERVER`|`U`|none|`\des+`|
|`LANGUAGE`|`U`|`U`|`\dL+`|
|`LARGE OBJECT`|`rw`|none||
|`SCHEMA`|`UC`|none|`\dn+`|
|`SEQUENCE`|`rwU`|none|`\dp`|
|`TABLE` (and table-like objects)|`arwdDxt`|none|`\dp`|
|Table column|`arwx`|none|`\dp`|
|`TABLESPACE`|`C`|none|`\db+`|
|`TYPE`|`U`|`U`|`\dT+`|