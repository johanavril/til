# Dry Run in Git

Some of git command allow us to check what would happen if we run the git command. We can prevent any accident by using `dry-run` flag on a git command. We can just do any normal git command and append `dry-run` flag to use it, the command will look like this:

```sh
git clean -d --dry-run
```

and the result will look like this:

```sh
Would remove git/
```
