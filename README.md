# do-git-seminar
A toy repo for helping peeps learn the ways of the git cli!

***Please consider forking this branch before you go through these exercises :D***

###Let's start fresh
```
> cd <$wherever>
> mkdir git-playground
> cd git-playground
> git init
```

## But what about remote things?!
###Clone a repo!
```
> git clone git@github.com:<user>/do-git-seminar.git
```
###Add a branch
```
> git checkout -b my-branch
```

###Add another branch!
```
> git checkout -b my-branch-2
```

This flow will make a git tree like this
```
master — my-branch — my-branch-2
```

but you probably don't want that. You might want this:
```
master — my-branch
    \
    my-branch-2
```

For that to happen, you would want to make sure you're on `master` before checking out `my-branch-2`

To do that...

###Go to a branch
```
> git checkout my-branch
```

###Make a file
```
> touch this-file.txt
```
You can see it has been made and it just chilling unstaged but running
```
git status
```

###Add a file
To start tracking this file and make sure it gets in your next commit
```
> git add this-file.txt
```

### Commit a file
```
> git commit -am ‘add a file!’
```

### Add another file!
For the sake of a future step, add another file and commit it!
```
> touch that-file.txt
> touch another-file.txt
> git add that-file.txt
> git add another-file.txt
> git commit -am ‘add more files’
```

###Push to remote
```
> git push origin my-branch
```

###Rebase! (DANGER!)
Rebasing will play your work on top of another branch. It's often cleaner than the merge workflow, but it's also more dangerous

We're gonna rebase "interactively (`-i`) on top of master so we can see what's going on. We'll want to play our work on top of the latest master, so fetching is likely necessary with a repo being used by a lot of people
```
> git fetch origin
> git rebase -i origin/master
```

###See your commit history
```
> git log
```
You'll see a list, in order of recency, of all of the commits in the branch

###Pushing a rebased branch to remote
In order to push your rebased branch to master, you're going to have to do something DANGEROUS: force (`-f`) push.

```
> git push -f origin ‘my-branch’
```

###Checkout another’s remote branch!
Fetch first so you have the most up-to-date version of the repo locally
```
> git fetch origin
```
You'll see a list of all the branches in the repo
```
> git checkout origin/<branch>
```
This will leave you in "detached head" mode, which essentially means you can't commit things. But, you can do
```
> git checkout <branch>
```
And you should get a version of the branch "tracking" the remote one that you can commit to and push to the remote branch from!
