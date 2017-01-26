# Pretty print JSON returned via Curl

When curling API endpoints and you get a large JSON payload it can be difficult to examine it without either copying and pasting to an editor or grepping.  Using this handy little Python utility will pretty print any returned JSON.

```bash
curl -v https://someapi-we-want-to-use | python -m json.tool
```

If you'd like to colourize the JSON output then you can achieve this with:

```bash
curl -v https://someapi-we-want-to-use | python -m json.tool | pygmentize -l json

```

However for the easiest time, add it all as an alias in `bash_aliases`

```bash
alias prettyjson='python -m json.tool | pygmentize -l json'
```