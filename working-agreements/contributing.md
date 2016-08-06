## Contributing

Guidelines for contributing code to
[coursereviews/coursereviews](https://github.com/coursereviews/coursereviews)
and other MiddCourses repositories.

### Flow

We follow a slightly amended [GitHub Flow](https://guides.github.com/introduction/flow/)
to add, review, and deploy code to MiddCourses. The essential difference is that our final
steps are merge, then deploy.

Suppose you're adding a new feature that allows users to view a list of their existing reviews.
Here's the general structure you'd use to add, test, and deploy that code.

#### 1. Branch from master

Always branch from the `master` branch to make sure the codebase you're about to contribute
to is up to date. Running `git status` lets you check where you are and that you don't have
any uncommitted changes sitting around.

```sh
$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working directory clean
```

Create and checkout a new branch for your feature. Good branch names are a word or two
describing the work you're doing there.

If you're worried about conflicting with existing branch names, check the
[branches page](https://github.com/coursereviews/coursereviews/branches)
or prefix the branch with your initials (eg. `ds/feature/list-reviews`).

```
$ git checkout -b feature/list-reviews
```

#### 2. Add some commits

Write the code to implement your change (make sure you write tests, too!) and commit the
changes. You can run `git add` multiple times. `git status` is your friend here to help add,
remove, stage, and unstage changes.

```sh
$ git add ... # where '...' are the paths to the files you changed
```

When you've `add`ed all the files that implement your change, commit the changes to Git.
Good commit messages are short and descriptive.

```sh
$ git commit -m "Add a user profile with a list of the user's reviews."
```

You're encouraged to write a longer, more explanatory message if necessary. If you want to
write more, omit `-m` and the commit message and Git will open up a text editor for you to
write a longer message. For the long message, sum up the commit on the first line, then leave
a blank line between the summary and long commit message. For example:

```
Add a user profile with a list of the user's reviews.

The new user profile page is reachable from a new button in the the navbar.
Professors do not see this button, as they can't write reviews.
```

#### 3. Push your branch

#### 4. Open a Pull Request

#### 5. Discuss and review the Pull Request with collaborators

#### 6. Make sure your test pass on the CI server

#### 7. Merge your changes into master

#### 8. Deploy master
