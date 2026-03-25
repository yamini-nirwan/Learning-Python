# Git Workflow Guide for Learning-Python Project

Welcome! This guide explains how to use Git effectively in this project. Git helps us track changes, collaborate safely, and maintain a clear history of our work.

## Table of Contents
1. [Before You Start](#before-you-start)
2. [Daily Workflow](#daily-workflow)
3. [Writing Good Commit Messages](#writing-good-commit-messages)
4. [Common Scenarios](#common-scenarios)
5. [Best Practices for Beginners](#best-practices-for-beginners)

---

## Before You Start

### Initial Setup

Before making your first commit, configure Git with your name and email:

```bash
# Set your name (this identifies you in commits)
git config --global user.name "Your Name"

# Set your email (should match your GitHub account if applicable)
git config --global user.email "your.email@example.com"

# Verify your settings
git config --global user.name
git config --global user.email
```

### Understanding the .gitignore File

Our `.gitignore` file tells Git which files to **ignore** (not track). This prevents accidentally committing:
- **Generated files**: `.csv` files (exported data from notebooks)
- **Virtual environments**: `venv/`, `env/` (specific to each machine)
- **Cache files**: `__pycache__/`, `.ipynb_checkpoints/` (Python and Jupyter cache)
- **IDE settings**: `.vscode/`, `.idea/` (personal editor preferences)

**Never manually edit `.gitignore` without understanding what you're doing!**

---

## Daily Workflow

### Step 1: Check the Current Status

Before making changes, see what Git is tracking:

```bash
# Shows which files are modified, new, or staged
git status
```

**Output explanation:**
- **Green files**: Ready to commit (staged)
- **Red files**: Modified but not staged, or new files not tracked

### Step 2: Make Your Changes

Work through your Python notebooks and scripts. Git will automatically notice changes when you save files.

### Step 3: Review Changes Before Committing

See exactly what you changed in a specific file:

```bash
# View changes in a single file
git diff general/Basic.ipynb

# View changes in all modified files
git diff
```

This helps you catch mistakes before committing.

### Step 4: Stage Your Changes

Staging tells Git which changes to include in the next commit. You typically stage changes related to one logical lesson or concept.

```bash
# Stage a single file
git add general/Basic.ipynb

# Stage all changes in the current directory
git add .

# Stage specific changes interactively (advanced, optional)
git add -p
```

### Step 5: Commit Your Changes

A commit is a snapshot of your staged changes. Always include a clear message explaining **what you learned, changed, or added**.

```bash
# Commit with a message
git commit -m "Add numpy array slicing examples"

# If you need more space to explain, use:
git commit
# This opens your default text editor for a longer message
```

### Step 6: Push to Remote (if applicable)

If working with a shared repository (like GitHub):

```bash
# Send your commits to the shared repository
git push origin main

# Or if you're on a different branch:
git push origin your-branch-name
```

---

## Writing Good Commit Messages

Great commit messages help you remember what you learned and when. Here's how to write them:

### Format

```
[Type] Brief title (max 50 characters)

Optional: Detailed explanation of what changed and what you learned.
```

### Types

- **Learn**: New concept or skill learned
- **Practice**: Practice exercises or examples added
- **Fix**: Bug fixed or mistake corrected
- **Refactor**: Code improved or reorganized
- **Docs**: Documentation or comments added
- **Chore**: Maintenance tasks (like organizing files)

### Examples

**Good commit messages:**
```
[Learn] Understand numpy array indexing and slicing

Practiced various ways to access and modify array elements.
Includes examples of basic indexing, slicing, and boolean indexing.

[Practice] Complete pandas data cleaning exercises

Implemented cleaning techniques including handling missing values,
removing duplicates, and basic data transformation.

[Docs] Add detailed comments to neural network code

Expanded docstrings and inline comments explaining each layer's
purpose and how backpropagation flows through the network.
```

**Bad commit messages (avoid these):**
```
"Updated code"  # Too vague - updated what?
"asdf"          # Not helpful
"WIP"           # Incomplete work shouldn't be committed
"Fixed stuff"   # Which stuff?
```

---

## Common Scenarios

### Scenario 1: You Modified a File But Don't Want to Commit Yet

```bash
# Save your work without committing it (temporary storage)
git stash

# Later, restore your changes:
git stash pop
```

### Scenario 2: You Made a Commit But Need to Fix It

```bash
# Undo the last commit but keep the changes (don't push yet!)
git reset --soft HEAD~1

# Then stage the corrected files and commit again
git add .
git commit -m "Fixed: [corrected message]"
```

### Scenario 3: You Want to See Previous Versions

```bash
# View the last 10 commits and their messages
git log --oneline -10

# See detailed information about a specific commit
git show abc1234

# View all changes to a specific file
git log -p general/Basic.ipynb
```

### Scenario 4: You Accidentally Committed a File from .gitignore

```bash
# Remove the file from Git tracking (but keep it locally)
git rm --cached data_file.csv

# Commit this change
git commit -m "Remove: Stop tracking generated CSV data"

# Future changes won't accidentally commit generated files
```

### Scenario 5: You Want to See What You Changed Recently

```bash
# Compare your current work to the last commit
git diff

# Compare a specific file to the last commit
git diff general/Computational.ipynb

# Compare your staging area (what's about to be committed)
git diff --cached
```

---

## Best Practices for Beginners

### ✅ Do This

- **Commit frequently**: Small, focused commits are easier to understand and review
- **Write meaningful messages**: Future you will thank you when reviewing old code
- **Test before committing**: Make sure your notebook cells run correctly before committing
- **Check status before committing**: Run `git status` to confirm you're committing the right files
- **Use descriptive variable names**: Remember, the code is for learning and teaching
- **Comment your code**: Include explanations of concepts as you learn them
- **Keep commits focused**: One commit = one topic or exercise, not multiple topics

### ❌ Don't Do This

- **Don't commit without messages**: Every commit needs a clear message
- **Don't commit generated files**: CSVs, cache files, etc. are handled by .gitignore
- **Don't use vague messages**: "Updated code" tells nobody anything useful
- **Don't commit broken notebooks**: Test cells before staging and committing
- **Don't commit large data files**: Keep learning datasets small or exclude them
- **Don't commit your virtual environment**: `.venv/` is ignored for a reason
- **Don't push without reviewing**: Always check your changes before pushing

### Helpful Git Aliases (Optional)

Add these to your Git config to save typing:

```bash
# View a pretty graph of commits
git config --global alias.graph 'log --graph --oneline --all'

# Show concise status
git config --global alias.st 'status -s'

# Undo last commit (careful!)
git config --global alias.undo 'reset --soft HEAD~1'
```

Then use them like:
```bash
git graph  # instead of git log --graph --oneline --all
git st     # instead of git status -s
```

---

## Key Reminders

1. **Git protects your learning**: You can always recover deleted commits or files (usually)
2. **Commits are immutable**: Once pushed, don't rewrite history without discussing with collaborators
3. **Branches are free**: Create branches to experiment without affecting main work
4. **Messages matter**: A clear commit message saves time when reviewing your progress
5. **Review before pushing**: Once pushed to shared repos, it's harder to change

---

## Getting Help

If something goes wrong:

```bash
# Undo the most recent change (if not pushed yet)
git reflog  # Shows all your recent actions

# Restore a file to a previous version
git checkout HEAD -- filename.py

# Ask Git for help on any command
git help commit
git help push
```

**Remember**: It's normal to make mistakes with Git. Everyone does! The more you practice, the more comfortable you'll become.

Happy learning! 🎓
