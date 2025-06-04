

``` javascript
//See webdev/future-upon-review/ur-backend/routes/api/review-api.js
const router = express.Router()
let db = require('./fs_pool.js');
const pool = db.getPool();

//This delete route requires checked foreign key for rev_id to
// have to cascade on delete
router.delete('/delete/:id', (req, res) => {
	const found = reviews.some(review => review.id === parseInt(req.params.id))
	if (found) {
		const id = parseInt(req.params.id)
		pool.connect((err, client, release) => {
			if (err) { return console.error('Error acquiring client', err.stack) }
			if (id) {
				client.query('DELETE FROM review as review WHERE review.id = $1', [id])
				res.json({
					msg: 'Review deleted', reviews: reviews.filter(
					review => review.id !== parseInt(req.params.id)
					)
				})
				release();
			}
			else {
			res.status(400).json({ msg: `No Review with the id of ${req.params.id} was found` })
			}
		})
	}
})
//See /webdev/future-upon-review/ur-backend/routes/db/fs_pool.js
const {Pool} = require('pg');
let pool;
const config = {
	user: process.env.USER,
	database: process.env.DATABASE,
	password: process.env.PASSWORD,
	port: process.env.DBPORT,
	host: process.env.DBHOST,
	max: 10,
	idleTimeoutMillis: 30000,
};
module.exports = {
	getPool: function () {
		if (pool) return pool; // if it is already there, grab it here
		pool = new Pool(config);
		return pool;
	},
}
```