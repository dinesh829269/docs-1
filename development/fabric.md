## Fabric

File: [fabfile.py](https://github.com/coursereviews/coursereviews/blob/master/fabfile.py)

Documentation: [fabfile.org](http://www.fabfile.org/)

### Deploy

```sh
$ fab deploy
```

Deploy to Heroku using Git, then check if migrations need to be run
and run them if necessary. While migrations are run the app is put
into [maintenance mode](https://devcenter.heroku.com/articles/maintenance-mode).

### Reset Database

```sh
$ fab reset_db
```

Drop the development database (`middcourses`) in the current running PostgreSQL instance.
Create a new database called `middcourses` and run migrations on it.

### List Databases

```sh
# Only databases beginning with "middcourses"
$ fab list_databases

# All databases
$ fab list_databases middcourses_only=false
```

Run from the command line to list all PostgreSQL databases beginning with "middcourses".
This is the default since the `fab capture_db` command prefixes the downloaded database with
"middcourses-". Useful to see the downloaded databases to set one and test the development
environment with the production database.

### Capture Database

```sh
$ fab capture_db
```

Create a backup of the production database using Heroku PG Backups.
Download the backup to a PostgreSQL dump file.
Restore the backup to the locally running PostgreSQL instance.
Optionally remove the dump file.
