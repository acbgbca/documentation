# Git

## Delete Merged Branches

```git for-each-ref --format '%(refname:short)' refs/heads --merged|grep -v "master\|main"|xargs git branch -d```

Explanation for each part:

Get a list of the branches that are merged into head
```git for-each-ref --format '%(refname:short)' refs/heads --merged```

Remove all branches named master or main
```grep -v "master\|main"```

Call 'git branch -d' with each merged branch to delete them
```xargs git branch -d```