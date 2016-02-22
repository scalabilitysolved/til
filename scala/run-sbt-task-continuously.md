# Run SBT task continuously

When using SBT sometimes you want to run a task such as compile or test continuously whenever SBT detects a file change, to achieve this just prepend the command with a `~` like so:

```bash
~test
```