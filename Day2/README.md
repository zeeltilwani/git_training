Scenario 1 – Wrong Branch Commit


Situation

Work was supposed to be done on feature/login

By mistake, the commit was made on main

The commit was not pushed yet

Goal

Move the commit to a feature branch and keep main clean.

Steps
1. Create a file and commit on main (mistake)
git checkout main
echo "Login feature code" > login.txt
git add login.txt
git commit -m "Added login feature"
2. Create feature branch from current commit
git branch feature/login
3. Switch to feature branch
git checkout feature/login
4. Remove commit from main
git checkout main
git reset --soft HEAD~1
5. Push feature branch
git checkout feature/login
git push -u origin feature/login
Result

Commit moved to feature/login

main history remains clean




Scenario 2 – Bad Commit Already Pushed



Situation

A wrong commit was pushed to main

The change needs to be undone

History must not be rewritten

Goal

Safely undo the commit using git revert.

Steps
1. Make a wrong commit
echo "Wrong config change" > config.txt
git add config.txt
git commit -m "Bad configuration change"
git push origin main
2. View commit history
git log --oneline

Example output

abc123 Bad configuration change
3. Revert the commit
git revert abc123
4. Push the fix
git push origin main
Result

A new commit is created that reverses the bad change

History remains intact and safe for teams




Scenario 3 – Merge Conflict in Team Environment
Situation



Working on feature/payment

Another developer updated the same file in main

Merge caused a conflict

Goal

Resolve the conflict manually and complete the merge.

Steps
1. Create feature branch
git checkout -b feature/payment
2. Modify file
echo "Payment logic v1" > payment.txt
git add payment.txt
git commit -m "Add payment logic"
3. Switch to main and modify same file
git checkout main
echo "Payment update from main" > payment.txt
git add payment.txt
git commit -m "Update payment logic in main"
4. Merge main into feature branch
git checkout feature/payment
git merge main

Git will show a merge conflict.

5. Identify conflict
git status
git diff

Conflict markers appear in the file:

<<<<<<< HEAD
Payment logic v1
=======
Payment update from main
>>>>>>> main
6. Resolve manually

Edit the file and remove markers:

Payment logic v1
Payment update from main
7. Complete merge
git add payment.txt
git commit -m "Resolve merge conflict"
8. Push updated branch
git push origin feature/payment
Key Concepts Learned

git reset --soft → Move commit without deleting changes

git revert → Safely undo pushed commits

git merge → Combine branches

Merge conflict markers (<<<<, ====, >>>>)

Proper feature branch workflow
