# Search terminal history easily

The history command within Linux is super useful displaying all your recently run commands for your current user:

Running `history` produces an output like:
```bash
 1004  git add .
 1005  git commit
 1006  git status
```

Running ! followed by the number in the history will re-run the command, all this is great but sometimes your history is huge, rather than piping and grepping your history all the time instead you can place this handy function in your `.bashrc` file:

```bash
h () { history | grep $1; }
```

This means now you can run `h SEARCH_TERM` and you'll get a filtered list of items from your terminal history that match the search term.