# Git Quick Reference Guide

A cheat sheet of the most common Git commands for this learning project. Keep this handy!

## Your Daily Commands (In Order)

```bash
# 1. See what changed
git status

# 2. View the actual changes (optional, but recommended!)
git diff

# 3. Stage changes for commit
git add .              # Stage everything
git add filename.py    # Stage one file

# 4. Create a commit snapshot
git commit -m "Describe your change here"

# 5. Push to shared repository (if applicable)
git push origin main
```

## Viewing History

```bash
# See recent commits
git log --oneline -10

# See changes in a specific file
git log -p filename.py

# See what changed in last commit
git show

# Compare current version to last commit
git diff
```

## Undoing Mistakes

```bash
# Unstage a file (keeps your changes)
git reset HEAD filename.py

# Undo changes to a file (loses changes!)
git checkout HEAD -- filename.py

# Undo last commit (keeps the changes)
git reset --soft HEAD~1

# View all recent actions (safety net!)
git reflog
```

## Working with Branches (if your team uses them)

```bash
# See all branches
git branch

# Create and switch to a new branch
git checkout -b learn/new-concept

# Switch to existing branch
git checkout main

# Delete a branch locally
git branch -d learn/old-concept
```

## Before Your First Commit (One-Time Setup)

```bash
# Tell Git who you are
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# Verify it worked
git config --global user.name
```

## What Files Are Ignored?

Check the `.gitignore` file to see what Git won't track. Examples in this project:
- `*.csv` - Generated data files
- `__pycache__/` - Python cache files
- `.ipynb_checkpoints/` - Jupyter notebook checkpoints
- `.vscode/` - Your personal editor settings
- `venv/` - Virtual environment

**These files won't appear in `git status` - that's intentional!**

## Pro Tips

```bash
# See a summary of changes before committing
git diff --stat

# Commit part of a file (only specific changes)
git add -p

# View what will be committed
git diff --cached

# See who changed each line (when debugging)
git blame filename.py
```

## Emergency Commands

```bash
# "I messed up and want to undo everything"
git reset --hard HEAD
# ⚠️ WARNING: This deletes all changes! Only use if desperate.

# "I need to get a file from an older commit"
git checkout abc1234 -- filename.py
# Replace abc1234 with the commit ID from git log

# "When did this bug get introduced?"
git bisect start  # Helps find which commit broke things
```

## Remember

- **Commit often**: Small commits are your safety net
- **Clear messages**: "Add numpy slicing examples" ✓ vs "Updated stuff" ✗
- **Check status**: `git status` is your friend!
- **Test first**: Make sure your notebook runs before committing
- **Push last**: Push to shared repo only when you're confident

---

## Confused? Check the Full Guide

See `git_workflow.md` for detailed explanations of each concept.

For Git documentation in your terminal:
```bash
git help commit
git help push
```

Happy learning! 📚
