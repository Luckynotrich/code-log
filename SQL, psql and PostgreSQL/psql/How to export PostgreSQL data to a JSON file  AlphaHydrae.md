##### [AlphaHydrae](https://alphahydrae.com/2021/02/how-to-export-postgresql-data-to-a-json-file/)
You know this data sitting in a PostgreSQL database that you have always wanted to export to a JSON file?

```
SELECT *
FROM people
WHERE meaning_of_life = 42;

--  id | name  | meaning_of_life
-- ----+-------+-----------------
--   1 | Alice |              42
--   2 | Bob   |              42
-- (2 rows)

```

Because PostgreSQL is awesome, it [supports JSON](https://www.postgresql.org/docs/13/datatype-json.html) and has [a lot of cool functions to work with JSON](https://www.postgresql.org/docs/13/functions-json.html). Let’s start by converting those rows to JSON objects using the `row_to_json` function:

```
SELECT row_to_json(people)
FROM people
WHERE meaning_of_life = 42;

--                  row_to_json
-- ----------------------------------------------
--  {"id":1,"name":"Alice","meaning_of_life":42}
--  {"id":2,"name":"Bob","meaning_of_life":42}
-- (2 rows)
```
You can now aggregate these rows into a JSON array with the `json_agg` [aggregation-function](https://www.postgresql.org/docs/13/functions-aggregate.html):
```
SELECT json_agg(row_to_json(people))
FROM people
WHERE meaning_of_life = 42;

-- Note: the result is represented on two lines here
-- for readability, but it's really one long line of
-- JSON in a single row:

--                     json_agg
-- ------------------------------------------------
--  [{"id":1,"name":"Alice","meaning_of_life":42},
--   {"id":2,"name":"Bob","meaning_of_life":42}]
-- (1 row)
```
Finally, convert this data to text and dump it to a file using [the `COPY` command](https://www.postgresql.org/docs/13/sql-copy.html):
```
COPY (
  SELECT json_agg(row_to_json(people)) :: text
  FROM people
  WHERE meaning_of_life = 42;
) to '/path/to/some/file.json';
```
And your JSON file is ready:
```
COPY (
  SELECT json_agg(row_to_json(people)) :: text
  FROM people
  WHERE meaning_of_life = 42;
) to '/path/to/some/file.json';
```
Easy as pie.

> Note that you can convert multiple rows into a JSON array with just `json_agg`, without using `row_to_json`, but for some reason converting that array to text will introduce line breaks into the resulting text, and the `COPY` command will serialize those line breaks into literal `\n` characters instead of actual line breaks.
> 
> To my knowledge there isn’t a configurable JSON stringification mechanism in PostgreSQL. It would be nice to have a function equivalent to [`JSON.stringify`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) that allows you to specify what kind of whitespace you want.