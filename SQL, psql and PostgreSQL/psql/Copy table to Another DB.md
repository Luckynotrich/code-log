output table as SQL file
```bash
pg_dump -C -d user-session -t session__user -f ./session_user.sql
```

Open output file in editor and edit the database name, also comment out the
'CREATE DATABASE' statement.
![[Pasted image 20240410154037.png]]
In this case from `user-session` to `future_self2`

Then run this command:
```bash
psql -d future_self2 -f ./session_user.sql 
```
PSQL complained about lucky already owning the database, so I probably could have commented out the 'ALTER DATABASE' line, but it still added the Table to the
