Advanced Git Commands
1. git checkout main -- <file>
What it does: Restores a file to the version from the main branch without touching other files.
When to use:
When you want to undo changes to one file.
When you don't want to reset the entire project.
What surprised me: It resets only one file and does not switch branches.

2. git cherry-pick <commit>
What it does: Takes one specific commit from another branch and applies it to your current branch.
When to use:
When you want only one fix/feature from a different branch.
When you don't want to merge a whole branch.
What surprised me: It copies the commit with a new ID and feels like selective merging.

3. git log
What it does: Shows all commit history with messages, dates, and authors.
When to use:
To understand how the project changed over time.
To find a commit you want to inspect or cherry-pick.
What surprised me: You can scroll and see every change made in the project.

4. git blame <file>
What it does: Shows who last modified each line in a file.
When to use:
Debugging: to ask the right person about a change.
Checking when a bug-related line was added.
What surprised me: It shows line-by-line authors, which is useful when many people edit the same file.