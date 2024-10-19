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
