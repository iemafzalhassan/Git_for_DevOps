## **8. Undoing and Fixing Mistakes**

### **Why Are Undo Commands Important in DevOps?**

In a DevOps environment, code mistakes can happen during updates, deployments, or testing. If a bug slips into production, knowing how to roll back changes quickly is crucial. Git’s undo commands—like `revert`, `reset`, and `clean`—are your safety nets, allowing you to fix errors and restore stability with minimal disruption.

---

### **1. Undoing Commits with `git revert`**

**`git revert`** creates a new commit that undoes changes from a previous commit. It’s like hitting “undo” but with a paper trail, so you can track what was removed.

#### **Why Use `git revert`?**

Imagine you’re working on a DevOps project, and a recent commit breaks part of the automation pipeline. Reverting lets you undo this specific change without disrupting the entire commit history, making it clear what was removed and why.

#### **Command and Usage**:
```bash
git revert <commit_hash>
```
- **Use Case**: Your team deployed an update that caused issues in production. To fix this, you revert the commit that introduced the problem, keeping history intact for tracking purposes.

#### **Flags**:
- `-n` (no-commit): Applies the revert without immediately committing, letting you make further adjustments if needed.
  
**Example**:
```bash
git revert -n 123abc
```
The command above reverts commit `123abc` without committing, so you can adjust before finalizing.

---

### **2. Resetting to a Previous State with `git reset`**

**`git reset`** is a more powerful tool that moves your branch pointer back to a previous commit. It can change the commit history or remove changes from the working directory.

#### **Why Use `git reset`?**

Consider a situation where you committed several development changes locally but realized they weren’t meant for the main branch. Resetting lets you “rewind” to an earlier commit, removing the unwanted changes from your history.

#### **Command and Usage**:
```bash
git reset <mode> <commit_hash>
```
- **Use Case**: You accidentally committed unfinished work on `main`. Use `reset` to remove this commit from the history and start fresh.

#### **Modes**:
- `--soft`: Keeps changes in the staging area, letting you recommit as needed.
- `--mixed` (default): Moves changes to the working directory without staging.
- `--hard`: Removes all changes, leaving no trace of them.

**Example**:
```bash
git reset --soft abc123
git reset --hard abc123
```
- **Soft reset** keeps the changes but removes the commit history.
- **Hard reset** erases everything after the specified commit—use with caution in shared branches!

---

### **3. Cleaning Untracked Files with `git clean`**

**`git clean`** is used to delete untracked files from your working directory. This is helpful when you want to remove unwanted files created during development or testing.

#### **Why Use `git clean`?**

Let’s say you’re testing new configurations in your local environment and have generated a lot of temporary files. `git clean` clears these files, restoring a tidy working state without affecting tracked files.

#### **Command and Usage**:
```bash
git clean <options>
```
- **Use Case**: You created some extra files during a test run that are cluttering your local environment. Using `clean` deletes them without touching the main project files.

#### **Options**:
- `-n` (dry-run): Shows what would be deleted without actually deleting.
- `-f` (force): Forces deletion of files.
- `-d`: Removes untracked directories as well.

**Example**:
```bash
git clean -n -f -d
```
- **Dry-run** shows the files that will be removed, while `-f -d` deletes them.

---

### **Real DevOps Scenarios for Each Command**

1. **Revert in Production Rollback**:
   - After a release, users report a bug. Instead of a full rollback, you can pinpoint the exact commit causing the issue and revert just that change, leaving other code intact.

2. **Reset During Development**:
   - During testing, you committed a series of unfinished changes. A `reset --soft` lets you remove these commits but keep the changes in your working directory so you can refine them without a messy history.

3. **Clean-Up After Testing**:
   - While testing new infrastructure configurations, temporary files are often created. Using `git clean` removes these files, keeping your environment free from clutter.

---

### **Summary of Commands and Flags for Undoing Changes**

| Command                 | Flags              | Description and Use Case                                                                                        |
|-------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------|
| `git revert <commit>`   | `-n`               | Creates a new commit that undoes changes from a prior commit. Ideal for tracking changes removed in production. |
| `git reset <mode>`      | `--soft`, `--hard` | Moves branch pointer to a previous commit. Useful for removing unwanted local commits.                          |
| `git clean`             | `-n`, `-f`, `-d`   | Deletes untracked files or directories. Helps remove temporary files generated during testing.                    |

---

### **Professional Tips for Safe Recovery**

- **Use Revert for Shared Branches**: When working on shared branches, `revert` is safer because it doesn’t rewrite history, which is essential in a collaborative DevOps environment.
  
- **Limit Reset to Local Changes**: Only use `reset` on local branches or commits you haven’t shared yet. Resetting on shared branches can disrupt other developers’ work.
  
- **Clean with Caution**: Always use `git clean -n` (dry-run) first to confirm what will be deleted, ensuring no important files are lost.
