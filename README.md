## Lab 1 — Setting Up Git & GitHub

```
git --version
git config --global user.name "Your Full Name"
git config --global user.email "yourname@example.com"
git config --list
mkdir git-lab-demo
cd git-lab-demo
git init
git status
ls -la
```

## Lab 2 — Basic Git Workflow

```
echo "print('Hello, Git!')" > hello.py
git status
git add hello.py
git status
git commit -m "Add hello.py with initial greeting script"
git log --oneline
git remote add origin https://github.com/<username>/git-lab-demo.git
git remote -v
git branch -M main
git push -u origin main
```

## Lab 3 — Creating and Managing Branches

```
git branch
git branch feature-branch
git switch feature-branch
echo "def add(a, b): return a + b" >> hello.py
git add hello.py
git commit -m "Add add() function on feature-branch"
git switch main
git merge feature-branch
git log --oneline --graph --all
git branch -d feature-branch
```

## Lab 4 — Pull Requests

```
git switch -c feature-readme
echo "# Git Lab Demo Project" > README.md
git add README.md
git commit -m "Add project README"
git push -u origin feature-readme
```

GitHub browser steps: Create Pull Request → Review changes → Merge Pull Request → Confirm merge.

```
git switch main
git pull origin main
```

## Lab 5 — Stashing Changes

```
echo "# work in progress" >> hello.py
git status
git stash push -m "WIP: work in progress on hello.py"
git status
git switch feature-readme
git stash list
git switch main
git stash pop
git status
git diff
```

Note: Replace `<username>` in Lab 2 with your actual GitHub username. Run Labs 1–5 in order, using the same repository.
