What caused the conflict?
The merge conflict happened because I changed the same line in the same file on two different branches:

One change was on the conflict-branch

Another change was on the main branch

Git did not know which version to keep, so it showed a conflict.

How I created the conflict
I made a new branch called conflict-branch

I edited a file and committed the change

I went back to the main branch and changed the same line in the file

When I tried to merge the two branches, Git showed a conflict

How I fixed the conflict
I used GitHub Desktop to solve the problem:

GitHub Desktop showed me both versions of the file

I chose which version I wanted to keep

I edited the file to remove the conflict markers

I marked the conflict as resolved

I committed the final version

What I learned
Merge conflicts happen when two branches change the same part of a file

Git cannot choose the correct version, so we must fix it manually

GitHub Desktop makes resolving conflicts easier

Pulling and committing regularly helps avoid big conflicts

