PostgreSQL
==========

createdb -U <db_user> <db_name>

Restore from dump
-----------------

    /usr/bin/pg_restore --host <host> --port 5432 --username "<username>" --dbname "<dbname>" --no-password  --verbose "./postgresql-db.1.pgdump"

HBA_info Live update
--------------------

    pg_ctl -D $PGDATA reload

More than 1 idle connection
---------------------------
    watch "psql -U <user> <db_name> -c ' SELECT client_addr, count(*)  FROM pg_stat_activity group by client_addr having count(*) > 1 order by c<db_name>  desc;'"
