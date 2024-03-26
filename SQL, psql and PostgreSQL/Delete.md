[Learn SQL](https://learnsql.com/blog/postgresql-delete-returning/)
The standard DELETE statement in SQL returns the number of deleted rows.

|                                                       |
| ----------------------------------------------------- |
| `DELETE` `FROM` `external_data;`<br><br>`DELETE` `10` |

In PostgreSQL you can make DELETE statement return something else. You can return all rows that have been deleted.

|                                                                                                                                                                                                                                                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `DELETE` `FROM` `external_data RETURNING *;`<br><br> `id \|        creation_date      \| user_id \|      data`<br><br>`----+---------------------------+---------+----------------`<br><br>`101 \| 2014-05-06 13:10:45.09484 \|    23   \|` `'Some text'`<br><br>`102 \| 2014-06-10 22:23:12.12045 \|    25   \|` `'Some other text'`<br><br>`(2` `rows``)`<br><br>`DELETE` `2` |

You can return the columns of your choice.

|                                                                                                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------- |
| `DELETE` `FROM` `external_data RETURNING id;`<br><br> `id`<br><br>`----`<br><br>`101`<br><br>`102`<br><br>`(2` `rows``)`<br><br>`DELETE` `2` |

In your code you can process the returned rows in the same way as you would process the results of an SQL query. For example, you may log the data that have been deleted.