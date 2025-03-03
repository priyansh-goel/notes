# PostgreSQL Backup & Restore

## Backup

To create a compressed backup of your PostgreSQL database:

```sh
pg_dump -Fc --no-owner --schema=public dbname > filename.dump
```

* `-Fc` : Custom format for better compression and flexibility
* `--no-owner` : Excludes ownership information (useful for restoring on a different user)
* `--schema=public` : Dumps only the public schema (modify as needed)

## Restore

To restore the backup to a PostgreSQL database:

```sh
pg_restore -U your_pg_user -j 4 -d dbname filename.dump
```

* `-U your_pg_user` : Specifies the PostgreSQL user
* `-j 4` : Uses 4 parallel jobs for faster restoration
* `-d dbname` : Specifies the target database

Ensure the target database exists before restoring. You can create it with:

```sh
createdb -U your_pg_user dbname
```

*Last updated: 2025-03-03*