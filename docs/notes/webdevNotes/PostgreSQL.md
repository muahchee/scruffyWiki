PostgreSQL
========================
## Single quotes (') and Double quotes(") mean different things

When inserting values with `VALUES`, for example - 
```
INSERT INTO usernames (username)
VALUES
  ('Oatchi'),
  ('Moss'),
  ('Olimar');
`;
```

When i use double quotes for `("Oatchi")`, i get the error `error: column "Oatchi" does not exist`.

Double quotes are for columns.

Single quotes are for rows.

## pg-format

https://www.npmjs.com/package/pg-format

```
var sql = format('SELECT * FROM %I WHERE my_col = %L %s', 'my_table', 34, 'LIMIT 10');
console.log(sql); // SELECT * FROM my_table WHERE my_col = '34' LIMIT 10
```

## pg_dump

[https://www.postgresql.org/docs/current/backup-dump.html](https://www.postgresql.org/docs/current/backup-dump.html)

can be used to create db backups

`pg_dump dbname > dumpfile` - creates an sql file to recreate database

`psql -X dbname < dumpfile` - restore db (remember to create the db first)

to dump a whole db cluster

`pg_dumpall > dumpfile'`

`psql -X -f dumpfile postgres`

## pg_ctl

[https://lab.uberspace.de/guide_postgresql/](https://lab.uberspace.de/guide_postgresql/)

do stuff with server

For Uberspace, dont start the server here. Start the server through `supervisorctl start postgresql`

Supervisorctl will automatically restart the server if it crashes.

## uberspace postgresql

updating db via internal script works fine. Cant get external connection string to work.

