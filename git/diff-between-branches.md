# Diff Between Branches

Git diff allow us to compare not only commits but also branches. The syntax is also the same, we just need to run git command like for the following example:

```sh
git diff feature-branch master
```

Git will compare the tips of both branches, we can also use `..` in between both branches and we will get the same result.

We can also know what changes occured on the second branch that is not on the first branch by using `...`. For example, the following command will find all changes occured on master that is not on feature-branch:

```sh
git diff feature-branch...master
```

We can even compare the branch with the upstream, and this mean we can also compare fork repository with the original repository. We just need to add the upstream in front of the branch name, it will look like this:

```sh
git diff feature-branch...upstream/master
```