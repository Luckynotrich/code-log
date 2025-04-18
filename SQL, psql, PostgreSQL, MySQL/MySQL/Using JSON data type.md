
# [ Insert and Select JSON Data in MySQL](https://www.youtube.com/watch?v=Bih5md-PRbs)
![[Pasted image 20250319133734.png]]
### Stringify to insert 
```js
const insert = (user) =>{

	const roles = JSON.stringify(user.roles);

	const result = pool.query('INSERT INTO user (user_name, user_roles, password, refreshtoken)' +
		' VALUES (?,?,?,?);', [user.username, roles, user.password, user.refreshToken ]);
	return result;
}
```

**CREATE TABLE**
```sql
DROP TABLE IF EXISTS user;
CREATE TABLE user(
	user_id INT AUTO_INCREMENT,
	user_name VARCHAR(50),
	user_roles JSON,
	password VARCHAR(97),
	refreshtoken VARCHAR(180),
	PRIMARY KEY (user_id)
);
```

**DATA**
```json
[
	{
		"username": "nicolecous@gmail.com",
		"roles": {
			"User": 2001,
			"Editor": 1962
		},
		"password": "$argon2id$v=19$m=65536,t=3,p=4$YHndPsF8T/JRKFOOamEn6g$FS9BOnkLbc4pFTFc2ZE9AKjsGKldXdZI3UuZZJq57lI",
		"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY29sZWNvdXNAZ21haWwuY29tIiwiaWF0IjoxNzM4NTk2NzA0LCJleHAiOjE3Mzg2ODMxMDR9.Gclu2omHPaiBU_fuDgMsBKumhwocz101RZ8_-L1pZcw"
	},
	{
		"username": "rich.rhaskell@gmail.com",
		"roles": {
			"User": 2001,
			"Editor": 1962,
			"Admin": 5440
		},
		"password": "$argon2id$v=19$m=65536,t=3,p=4$UZy9nZw8KfYzYtilDigIrw$amKw6Wl1savDU+sOcgVbHEb08UKS3mB2JIqKyq3D7xc",
		"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6InJpY2gucmhhc2tlbGxAZ21haWwuY29tIiwiaWF0IjoxNzM4NjIwNTk2LCJleHAiOjE3Mzg3MDY5OTZ9.cA1AVN3SaTtGiVsTdcpVKebJCLbKkzRvScImiBQITtc"
	},
	{
		"username": "nicole@newledohub.org",
		"roles": {
			"User": 2001
		},
		"password": "$argon2id$v=19$m=65536,t=3,p=4$y6cVssgd+etCzb4yrDZGCg$QKF5ISRttVPI2wdJ+l/IDO/5eilE5eo5qaHkCtmm2nE",
		"refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VybmFtZSI6Im5pY29sZUBuZXdsZWRvaHViLm9yZyIsImlhdCI6MTczODg2NjA2MSwiZXhwIjoxNzM4OTUyNDYxfQ.xEId55An9q8nB3geAgytmt_TEK1IK_tbw9qaZFVl2x4"
	}
]
```