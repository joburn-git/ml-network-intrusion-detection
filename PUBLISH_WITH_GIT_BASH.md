# Publish With Git Bash

Use these commands from Git Bash after reviewing the repository files.

```bash
cd "/c/Users/jober/Documents/Codex/2026-09-19/i-x20/outputs/ml-network-intrusion-detection"

git init
git add .
git commit -m "Add network intrusion detection project"
git branch -M main
```

If you use GitHub CLI:

```bash
gh repo create ml-network-intrusion-detection --public --source=. --remote=origin --push
```

If you create the repository manually on GitHub first:

```bash
git remote add origin https://github.com/YOUR-USERNAME/ml-network-intrusion-detection.git
git push -u origin main
```

Then add the text from `GITHUB_PROFILE_SNIPPET.md` to your GitHub profile README.
