#### MySQL's `UPDATE` statement does not directly support a `RETURNING` clause like some other SQL databases (like PostgreSQL). To get the updated data after an `UPDATE` in MySQL, you'll need to perform a separate `SELECT` query following the `UPDATE` statement, or use a trigger or stored procedure. 

Alternatives to RETURNING in MySQL:

1. **Separate SELECT:**
    - After your `UPDATE` statement, execute a `SELECT` query to retrieve the updated data.
    - Example:
```sql
     UPDATE products SET price = 12.99 WHERE product_id = 1;
     SELECT * FROM products WHERE product_id = 1;
```

**Triggers:**

- You can create a trigger that executes automatically after an `UPDATE` statement. 

- The trigger can then store the updated values in another table or return them to the application. 

- Example:
```sql
     CREATE TRIGGER before_update_products BEFORE UPDATE ON products
     FOR EACH ROW
     BEGIN
         INSERT INTO audit_log (old_value, new_value, table_name, column_name)
         VALUES (OLD.price, NEW.price, 'products', 'price');
     END;
```

