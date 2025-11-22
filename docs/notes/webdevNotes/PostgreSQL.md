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

## docker

oh my god this was such a headache

[https://www.youtube.com/watch?v=aHbE3pTyG-Q](https://www.youtube.com/watch?v=aHbE3pTyG-Q)

### commands to use postgres docker container

check images: docker images

check containers: docker ps

exit docker cont: ctrl-p ctrl-q
 
create container: docker run --name [name of container] -e POSTGRES_PASSWORD=[your password] -d -p 5432:5432 postgres

to run a shell: docker exec -it [name of container] sh

notes:
- `-p` exposes the port 5432
- without a password postgres wont work

## cron job backups

to add a cron job - `crontab -e`

[cron job ref](https://tecadmin.net/crontab-in-linux-with-20-examples-of-cron-schedule/)

adding a cronjob weekly - `@weekly /scripts/backup.sh`

```
// /scripts/backup.sh

pg_dump db_name > ~/pgbackup/`date '+%Y%m%d-%H%M'`-database.sql

```

`date` is a command that outputs a date

this outputs a file name like : `20251122-0012-database.sql`


## restore dump

1. check the sql file and remember to have the same user (username, pw) at the place you want to restore.

`CREATE USER username WITH PASSWORD 'password'`

2. also create a database for the new user.

`CREATE DATABASE username OWNER username`

3. then, create a target database for the dump with the previously created user as the owner

`CREATE DATABASE dumpdb OWNER username`

4. exit psql and restore the dump

`psql dumpdb < database_dump_file.sql`




