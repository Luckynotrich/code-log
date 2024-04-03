[Create Users Table ](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=392s)
```sql
	CREATE TABLE users(
	id BIGSERIAL PRIMARY KEY,
	name VARCHAR(60) NOT NULL,
	email VARCHAR(200) NOT NULL,
	password VARCHAR(200) NOT NULL
);
```

[update dashboard](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=1647s)

[Query database](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=3084s)

[Authenticate user](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=3985s)

```
listening on port 3000
http://localhost:3000/users/login:2024-03-29T15:10:34-07:00
/home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/node_modules/pg/lib/client.js:510
      throw new TypeError('Client was passed a null or undefined query')
            ^

TypeError: Client was passed a null or undefined query
    at Client.query (/home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/node_modules/pg/lib/client.js:510:13)
    at PendingItem.callback (/home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/passport-config.js:11:20)
    at BoundPool._acquireClient (/home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/node_modules/pg-pool/index.js:306:21)
    at BoundPool._pulseQueue (/home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/node_modules/pg-pool/index.js:151:19)
    at /home/lucky/webdev/passport-session/ur_user-api_passport-session-custom-callback/node_modules/pg-pool/index.js:184:37
    at process.processTicksAndRejections (node:internal/process/task_queues:77:11)

Node.js v20.9.0

```

[Adding logout](https://www.youtube.com/watch?v=vxu1RrR0vbw&t=4923s)
