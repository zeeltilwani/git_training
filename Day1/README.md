Git Practical Day1
1️⃣ Install Git

Checked Git installation:

git --version
2️⃣ Configure Git (Global & Local)
Global Configuration
git config --global user.name "Zeel Tilwani"
git config --global user.email "your-email@example.com"

Verify:

git config --global --list
Local Configuration (inside project)
git config user.name "Zeel Tilwani"
git config user.email "your-email@example.com"

Verify:

git config --list
3️⃣ Create Repository and Initial Commit

Create project directory:

mkdir git-training
cd git-training

Initialize Git:

git init

Create files:

touch README.md
touch app.py

Stage files:

git add README.md app.py

Commit:

git commit -m "Initial commit: Add README and app.py"

Check log:

git log --oneline --graph
4️⃣ Rename Branch to Main
git branch -M main
5️⃣ Connect to Remote Repository

Add remote:

git remote add origin https://github.com/zeeltilwani/git_training.git

Verify:

git remote -v

Push main branch:

git push -u origin main
6️⃣ Create Feature Branch

Create and switch branch:

git checkout -b feature/update-readme

Modify README.md and stage:

git add README.md

Commit changes:

git commit -m "Add feature branch section"

Push feature branch:

git push -u origin feature/update-readme
7️⃣ Create Pull Request

Open GitHub repository

Click Compare & Pull Request

Add title and description

Create Pull Request

Merge into main

Final Repository Status

Main branch created

Feature branch created

Changes committed

Pull Request created and merged

Git best practices followed
