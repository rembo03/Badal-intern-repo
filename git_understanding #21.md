Git Bisect 

1. What is git bisect?
git bisect is a tool that helps find which commit introduced a bug. Instead of checking every commit, Git uses binary search to quickly find the bad commit.

2. How it works (simple explanation)
Imagine the project has 100 commits and a bug appears. Instead of checking all 100 commits:
Git first checks the middle commit.
You test it.
If the bug is there → it’s bad.
If the bug is not there → it’s good.
Git then jumps again to the next middle commit.
After a few steps, Git finds the exact commit that caused the problem.

3. Commands used
git bisect start
git bisect bad
git bisect good <commit-id>
Then test each commit and mark:

git bisect good
git bisect bad
When Git finds the bad commit, reset:

git bisect reset
4. When to use git bisect in real projects
When a project is large and the bug’s origin is unknown.
When many developers push changes and you don’t know who caused the bug.
When something suddenly breaks after many merges.
When debugging manually would take too long.

5. What surprised me while testing
Git jumps between commits automatically.
It finds the bad commit very fast.
I don’t need to manually check every commit.
You can even automate bisect using scripts.

6. Summary
git bisect saves a lot of time, reduces guesswork, and makes finding bugs in long-running projects much easier.