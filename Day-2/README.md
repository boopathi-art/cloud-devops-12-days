# Day 2 – Git & GitHub Practice

## 📚 Topics Covered

- Git Clone
- Git Branch
- Git Commit
- Git Push
- Git Pull
- Git Remote
- Git Fetch
- Git Rebase
- Git Merge
- Git Stash

## 💻 Important Commands

```bash
# Clone repository
git clone <repository-url>

# Check status
git status

# Check branches
git branch

# Create branch
git branch <branch-name>

# Switch branch
git checkout <branch-name>

# Add changes
git add .

# Commit changes
git commit -m "message"

# Push changes
git push origin master

# Pull changes
git pull origin master

# Check remote
git remote -v

# Fetch changes
git fetch origin

# Rebase
git rebase master

# Merge branch
git merge <branch-name>

# Stash changes
git stash

# Restore stashed changes
git stash pop

```

## 🔄 Git Workflow

```text
GitHub Repository
       ↓
   git clone
       ↓
 Local Repository
       ↓
 Create / Switch Branch
       ↓
    Make Changes
       ↓
     git add
       ↓
   git commit
       ↓
   ┌───────┴───────┐
   ↓               ↓
 Rebase           Merge
   ↓               ↓
   └───────┬───────┘
           ↓
       git push
           ↓
        GitHub

```

## 🎯 Day 2 Learning

Today I practiced the Git and GitHub workflow, including cloning repositories, branch management, committing and pushing changes, merging branches, rebasing changes, and using Git stash to temporarily save uncommitted work.

## 🚀 Next Practice

- Git Stash in detail
- Merge conflicts
- Rebase conflicts
- Branch workflow
- Pull and push workflow
- GitHub collaboration workflow     add to into my github

