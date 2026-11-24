# Publish this portfolio to GitHub

## 1. Review the contents

Before making a public repository, review every file. The provided ZIP has been sanitized and does not include your actual SSH keys or private inventory. If you copy working files from `~/homelab/ansible`, check them for secrets and machine-specific addresses.

## 2. Extract the ZIP on Linux Mint

Use Archive Manager or a terminal to extract `home-lab-portfolio-starter.zip`. The extracted folder is `home-lab-portfolio`.

## 3. Initialize local version control

```bash
cd ~/Downloads/home-lab-portfolio  # Adjust to where you extracted it
git init -b main
git status
git add README.md .gitignore linux-server-administration ansible-nginx-automation docs
git diff --cached --stat
git commit -m "Add initial home lab project documentation"
```

If Git requests identity configuration, set `git config user.name "YOUR DISPLAY NAME"` and `git config user.email "YOUR PUBLIC OR NOREPLY EMAIL"` in the repository. Use a GitHub no-reply address if you want to avoid publishing your personal email in commits.

## 4. Create a repository on GitHub

Create an **empty** repository named `home-lab-portfolio` under your own account. Avoid initializing it with a README because this local folder already has one. Start it as **private** if you want to finish reviewing content before publishing.

Then use the HTTPS remote URL GitHub provides:

```bash
git remote add origin https://github.com/YOUR_USERNAME/home-lab-portfolio.git
git branch -M main
git push -u origin main
```

GitHub may ask you to sign in via a browser or credential helper; never paste passwords or personal access tokens into chat. Alternatively, connect the official GitHub app to work with repositories through ChatGPT after explicit authorization.

## 5. Add evidence carefully

Capture redacted terminal output and screenshots, update the project checklists, make commits for meaningful milestones, and then publish the repository if you want recruiters to view it.

## 6. Keep it updated

For every new project, create a dedicated folder using `docs/project-template.md`. Commit a concise explanation, reproducible sanitized files, results, and screenshots.
