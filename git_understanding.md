1. What is the difference between staging and committing?
Staging means selecting the changes you want Git to save later.
It’s like putting items into a basket at the shop but not buying them yet.

Committing means saving the staged changes permanently in Git history.
It’s like paying for the items — now they are officially recorded.

2. Why does Git separate these two steps?
Git keeps staging and committing separate because:

You can choose exactly which changes to save.

You can review your work before saving.

It helps you create clean and organized commits.

3. When would you stage changes without committing?
You might stage but not commit when:

You want to check your changes before saving.

You are still working but want to prepare some parts early.

You want to commit different changes separately instead of all together.

You need a moment to organize your work before making the final commit.

4. What I did during the experiment
I changed a file in my repo.

I used git add <file> to stage it.

I ran git status to see that the file was staged.

I used git reset HEAD <file> to unstage it.

Then I staged it again and used git commit -m "message" to commit it.

This helped me understand how staging and committing work differently.

