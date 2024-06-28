## 26.1. SQL Dump[](https://www.postgresql.org/docs/current/backup-dump.html#BACKUP-DUMP)
#### Exporting a PostgreSQL database

You can export a PostgreSQL database to a file by using the _pg_dump_ command line program, or you can use phpPgAdmin.

##### Method #1: Use the pg_dump program

To export a PostgreSQL database using the _pg_dump_ program, follow these steps:

1. Access the command line on the computer where the database is stored. For example, if the database is on another web hosting account or with another web hosting provider, log in to the account using SSH. If you have physical access to the computer, you can open a DOS or terminal window to access the command line.
2. Type the following command, and then press Enter. Replace _dbusername_ with a username that has permissions to access the database, and replace _dbname_ with the name of the database that you want to export:
    

pg_dump -U dbusername dbname > dbexport.pgsql