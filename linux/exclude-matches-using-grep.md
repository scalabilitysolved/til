# Exclude matches using Grep

Usually when using Grep I'm looking for a specific match or pattern, so use the standard:

```bash
grep search_term file
```

The ever great piping system means you can come up with some very flexible queries but today I really needed to exclude multiple matches from my results and here is how to do it:

```bash
grep -v -e searchTermOne -e searchTermTwo -e searchTermThree
```