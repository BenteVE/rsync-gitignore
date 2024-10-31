# rsync-gitignore

rsync cannot parse `.gitignore` files properly, so we can't simply use `rsync` with a `filter` or `exclude` option and indicate the `gitignore` files.
In this script, we will use `git ls-files` to list all ignored files for each encountered git repository.
We will write all those results to a file that we can use with the `rsync --exclude-from=FILE` option.
