va
syntax
```sql
ALTER TABLE table_name
RENAME TO new_table_name;
```
example
```sql
ALTER TABLE IF EXISTS table_name
RENAME TO new_table_name;
```

---

## ALTER COLUMN

We want to change the data type of the `year` column of the `cars` table from `INT` to `VARCAHR(4)`.

To modify a column, use the `ALTER COLUMN` statement and the `TYPE` keyword followed by the new data type:

### Example

Change the `year` column from `INT` to `VARCHAR(4)`:

```
ALTER TABLE cars  
ALTER COLUMN year TYPE VARCHAR(4);
```

## Add and Implement Sequence

For Postgres 9.6.24, while trans forming a database created in Postgres 16 it was necessary to create a sequence that would automatically generate id numbers and **Alter the table and column**.

This is sample code from [Stack Exchange](https://dba.stackexchange.com/questions/285869/add-auto-increment-to-already-existing-primary-key-column-postgresql)
```sql

create table t1 (id int primary key , x int);
insert into t1 values (1,1);
create sequence t1_Seq start with 2;

alter table t1 alter column id set  default nextval('t1_seq');

insert into t1 (x) values (2);

```

### Category table before operation
```bash
richar65_future_self3=> \d category
            Table "public.category"
  Column  |          Type          | Modifiers 
----------+------------------------+-----------
 id       | integer                | not null
 userid   | uuid                   | not null
 cat_name | character varying(100) | not null
Indexes:
    "category_pkey" PRIMARY KEY, btree (id)
    "userid_cat_name_unique" UNIQUE CONSTRAINT, btree (userid, cat_name)
Foreign-key constraints:
    "category_userid_fkey" FOREIGN KEY (userid) REFERENCES users(id)
Referenced by:
    TABLE "preference" CONSTRAINT "preference_cat_id_fkey" FOREIGN KEY (cat_id) REFERENCES category(id) ON DELETE CASCADE
    TABLE "review" CONSTRAINT "review_cat_id_fkey" FOREIGN KEY (cat_id) REFERENCES category(id)

```

This is the code I ran in psql. 
```sql
create sequence cat_id_seq start with 1;
alter table category alter column id set default nextval('cat_id_seq');

```
##### '**Start with 1' means the next entry will be 2**
### Category table after
```bash
richar65_future_self3=> \d category
                               Table "public.category"
  Column  |          Type          |                    Modifiers                     
----------+------------------------+--------------------------------------------------
 id       | integer                | not null default nextval('cat_id_seq'::regclass)
 userid   | uuid                   | not null
 cat_name | character varying(100) | not null
Indexes:
    "category_pkey" PRIMARY KEY, btree (id)
    "userid_cat_name_unique" UNIQUE CONSTRAINT, btree (userid, cat_name)
Foreign-key constraints:
    "category_userid_fkey" FOREIGN KEY (userid) REFERENCES users(id)
Referenced by:
    TABLE "preference" CONSTRAINT "preference_cat_id_fkey" FOREIGN KEY (cat_id) REFERENCES category(id) ON DELETE CASCADE
    TABLE "review" CONSTRAINT "review_cat_id_fkey" FOREIGN KEY (cat_id) REFERENCES category(id)

```

### Testing required adding a user
```sql
insert into users (email,password,user_name) values ('rich.rhaskell@gmail.com', '$2b$10$jf6aIIpO974uC9hMzQtGC.wGD0In49aLcwdDhSoI0IV2WX/vKxC6q' ,'luckyman');

insert into category (userid, cat_name) values ('9ebbf282-8eea-4b9f-a387-f070a2233357','Stuff');

```

#### Results
```bash
select * from category ;
 id |                userid                | cat_name 
----+--------------------------------------+----------
  2 | 9ebbf282-8eea-4b9f-a387-f070a2233357 | Stuff
(1 row)

```
