## Add a Term's Courses to the Database

### Get setup locally

0. Navigate to `coursereviews`
0. Make sure you're on the master branch (`git checkout master`) and the git status is clean (`git status`)
0. Activate the virtualenv: `workon coursereviews`
0. Log into Heroku from the command line: `heroku login`
0. Start Postgres.app
0. Download the latest production database: `fab capture_db`
0. Find the downloaded database with today's date and time: `fab list_databases` (something like "middcourses-2016-11-13T09:18:30")
0. Copy the complete name of this database and paste into the `NAME` value of `settings/local.py`.
0. Run the development server and make sure everything works.

### Scrape the courses locally

0. `python manage.py scrapecatalog --term 201690 --verbosity 2` [See the guide to term numbers.](term-numbers.md)
0. Start the server again and make sure everything looks good. Maybe check on a new professor or course.

### Scrape the courses in production

0. `heroku run python manage.py scrapecatalog --term 201690 --verbosity 2`
0. Visit [middcourses.com](www.middcourses.com) and make sure everything looks good.
