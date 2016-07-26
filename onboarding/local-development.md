## Local Development

For resource-specific documentation and tutorials see the [Additional Resources](https://github.com/middcourses/docs/blob/master/development/additional-resources.md).

Note: See the [Windows](https://github.com/middcourses/docs/blob/master/guides/windows.md) page for tooling specific to development on Windows.

### You need

* [PostgreSQL](http://postgresapp.com/): The PostgreSQL database engine. There are other ways to install PostgreSQL, but this is the easiest on OS X. Follow the [Postgres App instructions](http://postgresapp.com/documentation/cli-tools.html) to setup the `psql` command so you can use Postgres from the command line.

* Python 2.7. Install with [homebrew][homebrew] on OS X. See the [Python Guide](http://docs.python-guide.org/en/latest/starting/installation/) for more information.

* Python [Virtualenv][virtualenv]. Separates Python environments and dependencies for different projects. I use [virtualenvwrapper][virtualenvwrapper] to manage my virtual environments.

* [git][git]. Install with [homebrew][homebrew] on OS X.

Make sure you're using the Python you installed with Homebrew (not the system Python):

```
$ which python
/usr/local/bin/python

$ which pip
/usr/local/bin/pip
```

More information on package managers, Homebrew, and Python is [in the wiki](Package-Managers).

### Get the code

**Core Course Reviews and MiddCourses contributors**: You must enable [Two-Factor Authentication][2FA] before being added to the [Course Reviews](https://github.com/coursereviews) and [MiddCourses](https://github.com/middcourses) organizations.

Clone the repo:

Read up on [cloning via HTTPS or SSH][GitHub HTTPS] and how to deal with [2FA][2FA] from the command line. GitHub recommends cloning with HTTPS.

```sh
$ git clone https://github.com/coursereviews/coursereviews.git
```

Initialize a [virtualenv][virtualenv]:

```sh
$ mkvirtualenv coursereviews
```

Virtualenv should prepend the name if the environment in your command prompt. If it's not there
you can activate it with `workon coursereviews` and later deactivate it with `deactivate`.

Once you're in your virtual environment, install the Python requirements:

```sh
$ pip install -r reqs/development.txt
```

### Set up the database

Make sure PostgreSQL.app is running and create a development database:

```sh
$ fab reset_db
```

This will destroy the current development database if it exists and create a new one with the schema described in the [migrations][migrations].

The other [Fabric][fabric] commands are documented [here](https://github.com/middcourses/docs/blob/master/development/fabric.md).

### Start developing

Start the development server:

```sh
$ python manage.py runserver
```

As you work on the project, you can see your changes locally in your web browser by navigating to **localhost:8000**.

[homebrew]: http://brew.sh/ "Homebrew"
[virtualenv]: https://virtualenv.readthedocs.org/en/latest/ "Virtualenv"
[virtualenvwrapper]: https://virtualenvwrapper.readthedocs.org/en/latest/install.html#basic-installation "virtualenvwrapper"
[git]: http://git-scm.com/ "Git"
[migrations]: https://docs.djangoproject.com/en/1.9/topics/migrations/ "Django migrations"
[fabric]: http://www.fabfile.org/ "Fabric"
[GitHub HTTPS]: https://help.github.com/articles/which-remote-url-should-i-use/#cloning-with-https-urls-recommended
[2FA]: https://help.github.com/articles/about-two-factor-authentication/
