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
