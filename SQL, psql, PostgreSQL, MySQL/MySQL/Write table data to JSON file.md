```sh
mysql -u username -p database_name -e "SELECT JSON_ARRAYAGG(JSON_OBJECT('column1', column1, 'column2', column2)) AS data FROM your_table" > data.json 

mysql -u username -p database_name -e "SELECT JSON_ARRAYAGG(JSON_OBJECT('id', id, 'name', name)) AS data FROM contacts WHERE country='US'" > contacts_us.json
```