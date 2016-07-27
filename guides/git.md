## Git

### Useful Git Commands

#### Squash commits on a branch

This must be run from a branch that has been branched from `master`.
In the interactive editor, you can pick which commits to `pick`
and `squash`. There are instructions in the editor.

```sh
$ git rebase -i master
```

#### Clone from a remote (like GitHub)

This uses SSH. Check out the green "Clone or download" button on each
GitHub repo, too.

```sh
$ git clone git@github.com:coursereviews/coursereviews.git
```

#### Commit changes

Stage some files to commit them. Replace `.` with paths to files to track
in Git. You can only commit tracked files. Running this command as-is
(with `.`) will add all files in the project.

```sh
$ git add .
```

Actually commit the changes. Omit `-m "Some message."` to open an editor
where you can write a message. This is a good option if you have a longer,
multiline commit message.

```sh
$ git commit -m "Use AdminQuota object to get and set quota instead of hardcoding a value."
```

#### Create a new branch

Create a new branch:

```sh
$ git branch branch-name
```

Create a new branch and switch to it (a.k.a. `checkout` the branch):

```sh
$ git checkout -b branch-name
```

This is equivalent to:

```sh
$ git branch branch-name
$ git checkout branch-name
```
