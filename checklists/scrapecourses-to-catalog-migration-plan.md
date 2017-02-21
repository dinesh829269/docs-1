This document details the steps to migrate from using the [scrapecourses command](https://github.com/coursereviews/coursereviews/blob/feaa71a6f3f4538db35c3981ba775e5794ebde57/coursereviews/apps/reviews/management/commands/scrapecourses.py) to the [Catalog module](https://github.com/coursereviews/catalog) to add courses and professors to MiddCourses.

## Steps

1. Pad existing course codes with zeros between department and course code. For example `AMST101` becomes `AMST0101`. This is done with the new `padcoursecodes` command.

2. Run migrations to add the `midd_webid` column to the `reviews_professor` table. Run with `python manage.py migrate`.

3. Add Middlebury web ids to existing professors. In the official Middlebury catalog XML document, professors are identified by a 32-character web id. MiddCourses did not originally store these, identifying professors by email instead. The new catalog includes web ids but not emails. This step gets all current Middlebury faculty and stores their corresponding web id. This can be done with a single query to the Middlebury directory rather than hundreds of queries when the catalog is scraped. Run the new `scrapewebid` command to do this.

4. Scrape courses and professors with the new `scrapecatalog` command. `scrapecatalog` takes a term as an option. For example: `python manage.py scrapecatalog --term 201590` to scrape courses from Fall 2015.

## Commands

```sh
$ python manage.py padcoursecodes
$ python manage.py migrate
$ python manage.py scrapewebid
$ python manage.py scrapecatalog --term 201590
```
