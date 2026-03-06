Git Scenarios Practice
Scenario 1 – Wrong Branch Commit
Situation

A commit was made directly on main instead of feature/login. The commit was not pushed yet, so it needs to be moved to the correct branch.

Steps Performed

1️⃣ Check commit history

git log --oneline

2️⃣ Create new branch from current commit

git branch feature/login

3️⃣ Reset main to previous commit (remove the commit from main)

git reset --soft HEAD~1

4️⃣ Switch to feature branch

git checkout feature/login

5️⃣ Commit the changes on the correct branch

git commit -m "Added login feature"

6️⃣ Push the feature branch

git push -u origin feature/login
Concept

git reset --soft moves the commit but keeps changes staged.

Helps maintain clean branch workflow.

Scenario 2 – Bad Commit Already Pushed
Situation

A wrong configuration change was committed and already pushed to remote.
The change must be undone without rewriting history.

Steps Performed

1️⃣ Check commit history

git log --oneline

2️⃣ Revert the bad commit

git revert <commit-id>

3️⃣ Git creates a new commit that reverses the previous change.

4️⃣ Push the fix

git push origin main
Concept

git revert

Safely undoes a commit

Does not rewrite history

Recommended in team environments

Difference:

Command	Behavior
git reset	Rewrites history
git revert	Creates new undo commit
Scenario 3 – Merge Conflict in Team Environment
Situation

Two developers modified the same file in different branches.
While merging main into feature/payment, a merge conflict occurred.

Steps Performed

1️⃣ Switch to feature branch

git checkout feature/payment

2️⃣ Merge main branch

git merge main

3️⃣ Git reports merge conflict.

Check conflict status

git status

4️⃣ Identify conflicting files and view changes

git diff

5️⃣ Open the conflicted file and resolve manually.

Example conflict markers:

<<<<<<< HEAD
Your changes
=======
Main branch changes
>>>>>>> main

Remove the markers and keep the correct code.

6️⃣ Mark conflict as resolved

git add <filename>

7️⃣ Complete the merge

git commit -m "Resolved merge conflict"

8️⃣ Push updated branch

git push origin feature/payment
Concept

Merge conflicts occur when:

Multiple developers edit the same part of a file.

Conflict markers:

Marker	Meaning
<<<<<<< HEAD	Your branch code
=======	Separator
>>>>>>> main	Incoming branch code
Key Git Concepts Practiced

Branch workflow

Moving commits between branches

Safe undo using git revert

Merge conflict resolution

Team collaboration using Git
