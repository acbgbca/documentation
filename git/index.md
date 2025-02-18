# Git

## Set executable on a commited file

See https://stackoverflow.com/a/40979016

To change the executable flag on a file that has already been committed:
```git update-index --chmod=+x path/to/file```

To remove it:
```git update-index --chmod=-x path/to/file```

## Rebase a specific number of commits

To rebase a specific number of commits (I.e. 5) onto a specific branch (in this case main)
```git rebase -i HEAD~5 --onto main```

Useful if you created a feature branch off of the wrong branch, and you don't want to make sure only specific commits are bought across.

## Delete Merged Branches

```git for-each-ref --format '%(refname:short)' refs/heads --merged|grep -v "master\|main"|xargs git branch -d```

Explanation for each part:

Get a list of the branches that are merged into head
```git for-each-ref --format '%(refname:short)' refs/heads --merged```

Remove all branches named master or main
```grep -v "master\|main"```

Call 'git branch -d' with each merged branch to delete them
```xargs git branch -d```