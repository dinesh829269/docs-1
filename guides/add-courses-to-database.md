1. Navigate to `coursereviews`, make sure you're on the `master` branch, and activate the virtualenv.

```
$ git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.

$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean

$ workon coursereviews
(coursereviews) $
```

2. Log into Heroku from the command line: `heroku login`
3. Start Postgres.app
4. Download the latest production database: `fab capture_db`
5. Find the downloaded database with today's date and time: `fab list_databases` (something like "middcourses-2016-11-13T09:18:30")
6. Copy the complete name of this database and paste into the `NAME` value of `settings/local.py`.
7. Run the development server and make sure everything works.
