---
{"dg-publish":true,"permalink":"/linux-applications-and-cheat-sheets/git/git-pull-atlassian-git-tutorial/","tags":["git","tutorials"]}
---

[[ReadItLater\|ReadItLater]] [[Article\|Article]]

# [Git Pull | Atlassian Git Tutorial](https://www.atlassian.com/git/tutorials/syncing/git-pull)

## Git pull usage

### How it works

The `git pull` command first runs `git fetch` which downloads content from the specified remote repository. Then a `git merge` is executed to merge the remote content refs and heads into a new local merge commit. To better demonstrate the pull and merging process let us consider the following example. Assume we have a repository with a main branch and a remote origin.

![](https://wac-cdn.atlassian.com/dam/jcr:63e58c34-b273-4e48-a6b1-6e3ba4d4a0ea/01%20bubble%20diagram-01.svg?cdnVersion=2526)

In this scenario, `git pull` will download all the changes from the point where the local and main diverged. In this example, that point is E. `git pull` will fetch the diverged remote commits which are A-B-C. The pull process will then create a new local merge commit containing the content of the new diverged remote commits.

![](https://wac-cdn.atlassian.com/dam/jcr:0269bb2d-eb7f-43d8-80a2-8afa88d11eea/02%20bubble%20diagram-02.svg?cdnVersion=2526)

In the above diagram, we can see the new commit H. This commit is a new merge commit that contains the contents of remote A-B-C commits and has a combined log message. This example is one of a few `git pull` merging strategies. A `--rebase` option can be passed to `git pull` to use a rebase merging strategy instead of a merge commit. The next example will demonstrate how a rebase pull works. Assume that we are at a starting point of our first diagram, and we have executed `git pull --rebase`.

![Central git repo to local git repo](https://wac-cdn.atlassian.com/dam/jcr:d5633068-d448-4140-953e-2ab31553ce10/03%20bubble%20diagram-03-updated@2x%20kopiera.png?cdnVersion=2526)

In this diagram, we can now see that a rebase pull does not create the new H commit. Instead, the rebase has copied the remote commits A--B--C and rewritten the local commits E--F--G to appear after them them in the local origin/main commit history.

## Common Options

Fetch the specified remote’s copy of the current branch and immediately merge it into the local copy. This is the same as `git fetch ＜remote＞` followed by `git merge origin/＜current-branch＞`.

```
git pull --no-commit <remote>
```

Similar to the default invocation, fetches the remote content but does not create a new merge commit.

```
git pull --rebase <remote>
```

Same as the previous pull Instead of using `git merge` to integrate the remote branch with the local one, use `[git rebase](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase)`.

Gives verbose output during a pull which displays the content being downloaded and the merge details.

## Git pull discussion

You can think of `git pull` as Git's version of `svn update`. It’s an easy way to synchronize your local repository with upstream changes. The following diagram explains each step of the pulling process.

![git pull](https://wac-cdn.atlassian.com/dam/jcr:9c543e76-04df-429e-af48-43a5276d7f4f/04-06%20Git%20pull%20discussion.svg?cdnVersion=2526)

You start out thinking your repository is synchronized, but then `git fetch` reveals that origin's version of main has progressed since you last checked it. Then `git merge` immediately integrates the remote main into the local one.

## Git pull and syncing

`git pull` is one of many commands that claim the responsibility of 'syncing' remote content. The `[git remote](https://www.atlassian.com/git/tutorials/syncing)` command is used to specify what remote endpoints the syncing commands will operate on. The `[git push](https://www.atlassian.com/git/tutorials/syncing/git-push)` command is used to upload content to a remote repository.

The `git fetch` command can be confused with `git pull`. They are both used to download remote content. An important safety distinction can be made between `git pull` and `get fetch`. `git fetch` can be considered the "safe" option whereas, `git pull` can be considered unsafe. `git fetch` will download the remote content and not alter the state of the local repository. Alternatively, `git pull` will download remote content and immediately attempt to change the local state to match that content. This may unintentionally cause the local repository to get in a conflicted state.

## Pulling via Rebase

The `--rebase` option can be used to ensure a linear history by preventing unnecessary merge commits. Many developers prefer rebasing over merging, since it’s like saying, "I want to put my changes on top of what everybody else has done." In this sense, using `git pull` with the `--rebase` flag is even more like `svn update` than a plain `git pull`.

In fact, pulling with `--rebase` is such a common workflow that there is a dedicated configuration option for it:

```
git config --global branch.autosetuprebase always
```

After running that command, all `git pull` commands will integrate via `git rebase` instead of `git merge`.

## Git Pull Examples

The following examples demonstrate how to use `git pull` in common scenarios:

### Default Behavior

Executing the default invocation of `git pull` will is equivalent to `git fetch origin HEAD` and `git merge HEAD` where `HEAD` is ref pointing to the current branch.

### Git pull on remotes

```
git checkout new_featuregit pull <remote repo>
```

This example first performs a checkout and switches to the branch. Following that, the `git pull` is executed with being passed. This will implicitly pull down the newfeature branch from . Once the download is complete it will initiate a `git merge`.

### Git pull rebase instead of merge

The following example demonstrates how to synchronize with the central repository's main branch using a rebase:

```
git checkout maingit pull --rebase origin
```

This simply moves your local changes onto the top of what everybody else has already contributed.

###### Share this article