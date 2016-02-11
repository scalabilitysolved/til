# List branches in order of most recently created

When you end up with a lot of branches for a repo perhaps from context switching a lot it can be confusing as to which branch is the most recent, the following command lists the branches with the most recent first.

```bash
git for-each-ref --sort=-committerdate refs/heads/
```