1. What caused the conflict?
I changed the same line in a file on two different branches.
Git could not decide which version to keep.
So, a merge conflict happened.

2. How I created the conflict
Created a new branch: conflict-branch
Edited a file and committed it
Switched to main branch
Edited the same line differently
Tried to merge → Git showed a conflict

3. How I fixed the conflict
Opened GitHub Desktop
It showed both versions of the file
I chose the correct line to keep
Removed the conflict markers
Marked the conflict as resolved
Committed the final version

* What I learned
Merge conflicts happen when two branches edit the same part of a file
Git cannot automatically choose the correct version
We must fix the conflict manually
GitHub Desktop makes it easier to see and solve the conflict
Pulling and committing often helps avoid conflicts