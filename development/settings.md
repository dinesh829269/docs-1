## Settings

Settings configure the Django app to run. See the [complete documentation](https://docs.djangoproject.com/en/1.9/topics/settings/) on Django settings. Other settings may be specific to 3rd party packages we use (like [Pipeline](http://django-pipeline.readthedocs.org/en/latest/configuration.html)).

This document is about how we organize the settings for Course Reviews.

## Multiple settings files

We have different settings for running the app in different places. All the different settings files are stored in [coursereviews/settings](https://github.com/coursereviews/coursereviews/tree/8451a05ef6be331060a98c5e94d88a5a971154f6/coursereviews/settings).

Multiple settings for multiple environments is a common practice. Some reasons for this are: connecting a different database when we develop than when the app is running online; not sending real emails when we develop; adding debugging tools to the app for development only.

There are other files in *coursereviews/settings*, but the "top level" (meaning the ones that get used) are development, production, and testing:

- [development.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/development.py):
The settings used locally when you develop the app.
- [production.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/production.py): The settings used in production, where the app is deployed and available to the public. These are special because they reference a lot of keys not stored in any file, but rather in the production environment. It is important those keys are never made public, since they give the app access to the database and other integrated accounts (email, analytics, error reporting, etc.).
- [testing.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/testing.py): The bare settings required to get the app to run on the CI server. They are a cross between development and production.

The [common.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/common.py)
settings file is imported into each of the others. It contains the base of every settings file, with settings that are either common to all the environments, or are overridden in the environment specific file.

The [pipeline.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/pipeline.py) and [storage.py](https://github.com/coursereviews/coursereviews/blob/master/coursereviews/settings/storage.py) files contain settings that configure specific 3rd party integrations. It's convenient to store them in their own files.

### Local Settings

Sometimes you need settings locally that you don't want to commit. This is particularly useful when using a [captured database](https://github.com/coursereviews/coursereviews/wiki/Fabric#capture-database) instead of the default `middcourses` database.

To use a local database other than `middcourses`, create a file in [settings/](https://github.com/coursereviews/coursereviews/tree/master/coursereviews/settings) called *local.py* and insert a complete `DATABASES` setting like the one [here](https://github.com/coursereviews/coursereviews/blob/0e22c4f0e62de687838e9318382ec6322666f574/coursereviews/settings/development.py#L22-L31).

The development settings will attempt to import and use the `DATABASES` setting in *local.py*.

### Secrets

Don't store secret keys in settings files. It's a good practice to never put these in version control, whether the project is open source or not. Once it's in version control and pushed to the remote (here, GitHub), it's there forever.

<h3 align="center">
  <img src="https://media.giphy.com/media/zNXvBiNNcrjDW/giphy.gif">
</h3>

<p align="center"><i>Consequences</i></p>

If you haven't pushed yet there are ways to [rewrite git history](https://help.github.com/articles/remove-sensitive-data/), but it's best to not commit them in the first place.

Use different keys in development than the ones in production, or put them in the environment (`export KEY=VALUE`) and get them like we do in production (`os.environ.get('KEY', 'default value')`).
