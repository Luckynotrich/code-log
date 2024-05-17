```
13021169 rich.rhaskell@gmail.com
```

```
2024/05/15 12:48:30
error: no pg_hba.conf entry for host "106.0.62.69", user "richar65_lucky", database "richar65_future_self2", SSL off
    at /home/richar65/nodevenv/futureonreview.com/20/lib/node_modules/pg-pool/index.js:45:11
    at process.processTicksAndRejections (node:internal/process/task_queues:95:5)
    at async PGStore._asyncQuery (/home/richar65/nodevenv/futureonreview.com/20/lib/node_modules/connect-pg-simple/index.js:321:21)

```

```env
NODE_ENV=development
SERVER='az1-ts106.a2hosting.com'
PASSWORD=lNcd@O?5IcUl
DB_USER=richar65_lucky
DATABASE= richar65_future_self2
DB_PORT=5432
DB_HOST= "az1-ts106.a2hosting.com"
SECRET=luck rich nought $ rich
```

```
/home/richar65/futureonreview.com/app.js:114
    if (err) { return next(err); }
                      ^

TypeError: next is not a function
```
