# Copying and pasting in VIM

Vim is a super handy terminal editor but outside of the main commands it's easy to forget some of the other shortcuts.  To copy and paste the following can be used

```bash
v <- to select characters
V <- to select lines
d <- cut current selection
y <- copy (yank) current selection

Move the cursor to the destination location
p <- paste selection after the cursor
P <- paste selection before the cursor