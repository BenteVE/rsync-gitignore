# rsync-gitignore

`rsync` cannot parse `.gitignore` files properly due to negation patterns and patterns that should apply to nested folders.

In this script, we will use `git ls-files` to list all ignored files for each encountered git repository.
We will write all those results to a file that we can use with the `rsync --exclude-from=FILE` option.
This solution should work for both simple git repositories, and for folders containing multiple git repositories at different levels of nesting.

Note that this particular implementation also copies the `.git` folder(s) to the destination and uses `--delete-excluded` to remove any files from the destination that are not in the source.
