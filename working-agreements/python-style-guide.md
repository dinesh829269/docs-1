## Python Style Guide

Code needs to pass the linter. The CI will run the linter, so it's a good idea to run it locally to catch changes before you push.

We use [flake8](http://flake8.pycqa.org/en/latest/) to lint our Python code.

Install flake8 with:

```sh
$ pip install flake8
```

Run the linter with:

```sh
$ flake8
```

Generally we follow [PEP 8](https://www.python.org/dev/peps/pep-0008/), "The Style Guide for Python Code", with the following exceptions:

 - Ignore E302 (expected 2 blank lines, found 1)
 - Line length 100 characters
