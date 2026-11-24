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
## lab 6 CLONING A REMOTE REPOSITORY
cd ..
git clone https://github.com/<username>/git-lab-demo.git git-lab-demo-clone
cd git-lab-demo-clone
git remote -v
git branch -a
git log --oneline

## lab-7 FETCH AND REBASE

echo "Local change" >> hello.py
git add hello.py
git commit -m "Local change before rebase"
git fetch origin
git log --oneline main
git log --oneline origin/main
git rebase origin/main
git log --oneline --graph
git push --force-with-lease origin main

## lab-8 RESOLVING MERGE CONFLICTS
git switch main
git switch -c branch-a
echo "Version: A" > version.txt
git add version.txt
git commit -m "Set version to A on branch-a"

git switch main
git switch -c branch-b
echo "Version: B" > version.txt
git add version.txt
git commit -m "Set version to B on branch-b"

git switch main
git merge branch-a
git merge branch-b

echo "Version: A+B merged" > version.txt
git add version.txt
git commit -m "Resolve merge conflict in version.txt"
git log --oneline --graph --all

## lab-9 GIT TAGS AND RELEASES

git log --oneline
git tag v1.0
git tag v0.9 <commit-hash>
git tag
git show v1.0
git push origin v1.0

## lab-10 ADVANCED OPERATIONS – CHERRY-PICK, RESET AND REVERT
git switch -c bugfix-branch
echo "def subtract(a, b): return a - b" >> hello.py
git add hello.py
git commit -m "Add subtract() function"
git log --oneline -1
git switch main
git cherry-pick <commit-hash>
git log --oneline

echo "temp change" >> hello.py
git add hello.py
git commit -m "Temporary commit to demonstrate reset"
git reset --soft HEAD~1
git status
git reset --mixed HEAD
git status
git reset --hard HEAD
git status

echo "faulty change" >> hello.py
git add hello.py
git commit -m "Introduce a faulty change"
git log --oneline -1
git revert HEAD
git log --oneline --graph

## lab-11 GITHUB COLLABORATION TOOLS – ISSUES AND WIKI

git commit -m "Add input validation to add() function – Fixes #1"

## lab-12 ANALYSING GIT HISTORY
git log
git show <commit-hash>
git log -1 <commit-hash>
git log --author="Your Full Name"
git log --author="Vinit Kumar Shukla" --oneline
git log --since="2026-01-01" --until="2026-12-31"
git log --after="2026-08-01" --before="2026-08-31"
git log --since="2026-01-01" --until="2026-12-31" --oneline
git log --author="Your Full Name" --since="1 month ago"
git log -5
git log --oneline -n 5
git log --pretty=format:"%h | %an | %ad | %s" --date=short -5
git log --oneline --graph --all --decorate
Note: Replace `<username>` in Lab 2 with your actual GitHub username. Run Labs 1–5 in order, using the same repository.
