# **Comprehensive Git & DevOps Commands for Professionals**

This guide provides a complete list of essential, advanced, and DevOps-specific Git commands. It’s tailored for professionals working in environments where Git is essential for version control, collaboration, and continuous integration/delivery.

---

## **Basic Git Commands (Foundation):**

### 1. **Initialize a New Repository**
   - **Command:** `git init`
   - **Usage:** Initializes a new Git repository in your current directory to begin version control.

### 2. **Clone an Existing Repository**
   - **Command:** `git clone <repository-url>`
   - **Usage:** Creates a copy of an existing repository to your local machine.

### 3. **Check Repository Status**
   - **Command:** `git status`
   - **Usage:** Displays the state of the working directory, showing untracked files, staged changes, and modifications.

### 4. **Add Files to Staging Area**
   - **Command:** `git add <file>` or `git add .`
   - **Usage:** Stages changes for the next commit.

### 5. **Add Only Parts of a File to Staging**
   - **Command:** `git add -p <file>`
   - **Usage:** Interactively stages specific portions (hunks) of a file, ideal for partial commits.

### 6. **Commit Changes**
   - **Command:** `git commit -m "Commit message"`
   - **Usage:** Records changes to the local repository.

### 7. **View Commit History**
   - **Command:** `git log`
   - **Usage:** Shows the commit history.

### 8. **Create a New Branch**
   - **Command:** `git branch <branch-name>`
   - **Usage:** Creates a new branch for development.

### 9. **Switch Branches**
   - **Command:** `git checkout <branch>`
   - **Usage:** Switches to another branch.

### 10. **Push Changes to a Remote Repository**
   - **Command:** `git push origin <branch>`
   - **Usage:** Pushes local commits to a remote repository.

### 11. **Pull Changes from Remote Repository**
   - **Command:** `git pull origin <branch>`
   - **Usage:** Fetches and merges changes from a remote repository.

### 12. **Merge Branches**
   - **Command:** `git merge <branch>`
   - **Usage:** Merges the changes from one branch into another.

---

## **Advanced Git Commands (Professional Expertise)**

### 1. **Amend the Last Commit**
   - **Command:** `git commit --amend --no-edit`
   - **Usage:** Modifies the last commit without changing the commit message.

### 2. **Interactive Rebase**
   - **Command:** `git rebase -i HEAD~5`
   - **Usage:** Clean up commit history by reordering or squashing commits.

### 3. **Stashing Changes**
   - **Command:** `git stash` or `git stash save "message"`
   - **Usage:** Temporarily saves your changes without committing.

### 4. **Stash Only Specific Parts of Files**
   - **Command:** `git stash push -p`
   - **Usage:** Stash specific changes in a file interactively.

### 5. **Cherry-Pick Commits**
   - **Command:** `git cherry-pick <commit-hash>`
   - **Usage:** Apply a specific commit from another branch.

### 6. **Undo Changes with Reflog**
   - **Command:** `git reflog`
   - **Usage:** Tracks actions in Git, even those not in history, useful for recovering lost commits.

### 7. **Find a Bug with Git Bisect**
   - **Command:** `git bisect start`
   - **Usage:** Perform a binary search to find the exact commit that introduced a bug.

### 8. **Sparse-Checkout for Large Repos**
   - **Command:** `git sparse-checkout init --cone && git sparse-checkout set <folder>`
   - **Usage:** Only check out a portion of a large repository.

### 9. **Sign Commits for Verification**
   - **Command:** `git commit -S -m "Commit message"`
   - **Usage:** Sign your commits with a GPG key for secure verification.

### 10. **Push with Lease to Avoid Overwrites**
   - **Command:** `git push --force-with-lease`
   - **Usage:** Force push your changes while preventing overwriting someone else’s work.

### 11. **Use Custom Merge Tools**
   - **Command:** `git config merge.tool <tool>`
   - **Usage:** Specify a custom merge tool to visually resolve conflicts.

---

## **DevOps-Specific Git Commands (Automation & CI/CD)**

### 1. **Git Tags for Versioning**
   - **Command:** `git tag -a v1.0.0 -m "Version 1.0"`
   - **Usage:** Create an annotated tag for versioning your releases in CI/CD pipelines.
   - **Command:** `git push origin v1.0.0`
   - **Usage:** Push the tag to the remote repository.

### 2. **Deploy Changes with CI/CD Systems**
   - **Command:** `git push origin <branch> --tags`
   - **Usage:** Push changes and tags together for triggering deployments in CI/CD systems like Jenkins, GitLab CI, or GitHub Actions.

### 3. **Automation with Hooks**
   - **Command:** `vi .git/hooks/pre-commit`
   - **Usage:** Automate tasks like running tests or linting code before committing by configuring Git hooks.

### 4. **Checking for Large Files (To Optimize Repos)**
   - **Command:** `git rev-list --objects --all | sort -k 2 | cut -f1 | xargs git cat-file -s | sort -n -r | head -n 10`
   - **Usage:** Lists the top 10 largest files in your Git history to optimize repository size.

### 5. **Git Submodules for Infrastructure Repos**
   - **Command:** `git submodule add <repository-url>`
   - **Usage:** Use Git submodules to manage external dependencies in infrastructure-as-code repositories (e.g., Terraform, Ansible).

### 6. **Continuous Deployment using GitLab CI/CD**
   - **Command:** `.gitlab-ci.yml`
   - **Usage:** Define a `.gitlab-ci.yml` configuration file to automate testing, building, and deploying code in a GitLab CI/CD pipeline.

### 7. **Using Git Worktrees for Multi-Environment Workflows**
   - **Command:** `git worktree add <path> <branch>`
   - **Usage:** Use Git worktrees to work on multiple branches simultaneously, useful in multi-environment deployments (e.g., development, staging, production).

### 8. **Deploy via GitHub Actions**
   - **Command:** `.github/workflows/deploy.yml`
   - **Usage:** Use GitHub Actions by defining deployment workflows in YAML, automating the deployment process for your infrastructure.

### 9. **Handling Hotfixes with Cherry-Pick**
   - **Command:** `git cherry-pick <commit-hash>`
   - **Usage:** Apply hotfixes to production branches without merging an entire feature branch.

### 10. **Environment-Specific Configurations with Branch Strategies**
   - **Command:** `git branch -m development`
   - **Usage:** Maintain different branches for environments (e.g., development, staging, production) and switch between them as needed.

### 11. **GitLab CI with Docker for Continuous Deployment**
   - **Command:** `docker build -t <image> . && docker run <image>`
   - **Usage:** Use GitLab CI and Docker to automate building and deploying Docker containers in CI/CD pipelines.

### 12. **GitOps with Infrastructure Repos**
   - **Command:** `git push origin master`
   - **Usage:** Apply GitOps principles by pushing changes to a repository that triggers infrastructure automation and deployment.

---

## **Git Aliases for DevOps Efficiency**

### 1. **Creating Shortcuts for Frequently Used Commands**
   - **Command:** `git config --global alias.co checkout`
   - **Usage:** Create aliases to speed up repetitive tasks.

### 2. **Alias for Deployments**
   - **Command:** `git config --global alias.deploy '!git push origin master --tags && ssh user@server "cd /path/to/project && git pull && restart-service"'`
   - **Usage:** Automate deployments with a single alias.
