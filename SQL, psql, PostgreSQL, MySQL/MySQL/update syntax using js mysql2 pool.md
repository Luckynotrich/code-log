```js
const mysql = require('mysql2/promise');

async function updateData(pool, table, data, whereCondition) {
  try {
    const connection = await pool.getConnection();

    // Construct the SET clause for the UPDATE query
    const setClause = Object.keys(data)
      .map((key) => `\`${key}\` = ?`)
      .join(', ');

    // Prepare the SQL query
    const sql = `UPDATE \`${table}\` SET ${setClause} WHERE ${whereCondition}`;

    // Execute the query with the data values
    const [result] = await connection.execute(sql, Object.values(data));

    connection.release();

    return result;
  } catch (error) {
    console.error('Error updating data:', error);
    throw error;
  }
}

// Example usage:
const pool = mysql.createPool({
  // ... Pool configuration
});

const table = 'users';
const dataToUpdate = { name: 'John Doe', email: 'john.doe@example.com' };
const whereClause = 'id = 1'; 

updateData(pool, table, dataToUpdate, whereClause)
  .then(result => {
    console.log('Update successful:', result);
  })
  .catch(error => {
    console.error('Update failed:', error);
  });
```