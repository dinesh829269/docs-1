## Testing

New code should have tests to verify it works as expected.

Write tests for old, previously untested, code as you are able.

If you uncover and fix a bug, write tests to ensure it stays fixed.

### Continuous Integration (CI)

Whenever you push code to GitHub (the Git remote) or open a Pull Request, the
[CI](https://travis-ci.org/coursereviews/coursereviews) will run the linter
and the tests using the commands in
[.travis.yml](https://github.com/coursereviews/coursereviews/blob/master/.travis.yml).
The tests should pass on the CI before you merge a pull request into the master branch
and deploy to production.

### Testing Resources

* [Testing in Django](https://docs.djangoproject.com/en/1.9/topics/testing/):
  Most of your tests will be written in Python and use Django's test framework.
  This is a good starting place.
