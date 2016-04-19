# Find unique matches from partial line matches using Grep

Using Grep sometimes you want to find unique instances of a particular detail within a file, give the excerpt of logs below:

```text
2016-04-19 12:32:55,888 [INFO] application - some-cache-key-or-interesting-thing
2016-04-19 12:32:55,954 [INFO] application - company::1232
2016-04-19 12:32:56,459 [INFO] application - some-cache-key-or-interesting-thing
2016-04-19 12:32:56,469 [INFO] application - company::1232
```

If you want to find all unique strings after then usually you'd reach for something like:

```bash
grep INFO | sort | uniq
```

However this would just output all the lines from above as the sort and uniq functions operate on the whole string and thus the timestamp makes each line unique.  To do a partial select in grep you can use the `-o` flag like so:

```bash
grep -o INFO
```

However that'll only output the exact search term so we'll end up with 4 instances of `INFO` and thus no real information that we need. To achieve what we want we need to wildcard match on our search term and *then* apply our sort and uniq functions.  The following works and will output unique data and disregarding the timestamp:

```bash
grep -o 'INFO.*' FILE_NAME | sort | uniq
```