#### Creating a new PostgreSQL database and assigning a user

Before you can import the database, you must create a new database in cPanel and assign a user to it. To do this, follow these steps:

1. Log in to cPanel.
    
    If you do not know how to log in to your cPanel account, please see [this article](https://www.a2hosting.com/kb/cpanel/getting-started-with-cpanel/accessing-cpanel).
    
2. Open the PostgreSQL Databases tool:
    - If you are using the **Jupiter** theme, on the Tools page, in the Databases section, click PostgreSQL Databases:
        
        ![cPanel - Databases - PostgreSQL Databases icon](https://www.a2hosting.com/images/uploads/knowledgebase_images/kb-cpanel-jupiter-databases-postgresql-databases-icon.png)
    
3. Under Create New Database, in the Database Name text box, type the name of the database.  
    
    You cannot use capital letters in a PostgreSQL database name.
    
- Click Create Database.
- When the database is created, click Go Back.
- Under Add User to Database, in the User list box, select the user that you want to add.
- In the Database list box, select the new database.
- Click Submit.
#### Exporting a PostgreSQL database

You can export a PostgreSQL database to a file by using the _pg_dump_ command line program, or you can use phpPgAdmin.

##### Method #1: Use the pg_dump program

To export a PostgreSQL database using the _pg_dump_ program, follow these steps:

1. Access the command line on the computer where the database is stored. For example, if the database is on another web hosting account or with another web hosting provider, log in to the account using SSH. If you have physical access to the computer, you can open a DOS or terminal window to access the command line.
2. Type the following command, and then press Enter. Replace `dbusername`with a username that has permissions to access the database, and replace `dbname` with the name of the database that you want to export:
    

```sh

pg_dump -U dbusername dbname > dbexport.pgsql

```
3. Type your A2 Hosting account password at the Password prompt.
4. The `dbexport.pgsql` file now contains all of the data for the `dbname` database. If the `dbexport.pgsql` file is on a remote computer, download the file to your local computer.


#### Importing a PostgreSQL database

After you have created a new database in cPanel, you can import the database's contents by using the _psql_ command line program, or you can phpPgAdmin.

You should import all PostgreSQL data as the **primary** PostgreSQL user (that is, by using your domain username). If you import PostgreSQL data as a regular user, you will be unable to see or manipulate the data properly using phpPgAdmin. After you have imported the data as the primary PostgreSQL user, you can grant a regular user access to the data. Then you do not have to use the primary domain username and password in scripts that access the database.

##### Method #1: Use the psql program

To import a PostgreSQL database using the _psql_ program, follow these steps:

1. Transfer the `dbexport.pgsql` file to your A2 Hosting account using `SCP`,` SFTP`, or FTP.
2. Log in to your A2 Hosting SSH account.
3. Type the following command, and then press Enter. Replace _username_ with your username and replace _`dbname`_ with the name of the database that you want to import the data into:
    

```sh
psql -U username dbname < dbexport.pgsql
```

4. The `dbname` database should now contain the data that is in the `dbexport.pgsql`  file.