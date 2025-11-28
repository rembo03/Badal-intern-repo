Basic Git Operations & Functionality
This document summarizes the essential Git commands and concepts I learned as part of my internship tasks. These operations form the foundation for working with any codebase in a professional environment.

✅ 1. Git Initialization
Initialize a new Git repository
bash
Copy code
git init
Used to start version control in a new project.

Clone an existing repository
bash
Copy code
git clone <repo-url>
Creates a local copy of a remote GitHub repository.

✅ 2. Checking Status
View current changes in the project
bash
Copy code
git status
Shows modified, staged, and untracked files.

✅ 3. Staging & Committing
Add files to the staging area
bash
Copy code
git add <file>
Add all files
bash
Copy code
git add .
Commit changes with a message
bash
Copy code
git commit -m "Your commit message"
✅ 4. Branching & Switching
List all branches
bash
Copy code
git branch
Create a new branch
bash
Copy code
git branch feature-name
Switch to a branch
bash
Copy code
git checkout feature-name
Create & switch in one step
bash
Copy code
git checkout -b feature-name
✅ 5. Working With Remote Repositories
Add remote origin
bash
Copy code
git remote add origin <repo-url>
Push changes
bash
Copy code
git push
Push to a specific branch
bash
Copy code
git push origin main
Pull the latest changes
bash
Copy code
git pull
✅ 6. Merging
Merge another branch into the current one
bash
Copy code
git merge <branch-name>
✅ 7. Undoing Changes
Unstage a file
bash
Copy code
git reset <file>
Discard changes in a file
bash
Copy code
git checkout -- <file>
Undo last commit but keep changes
bash
Copy code
git reset --soft HEAD~1