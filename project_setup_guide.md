## Collaborator Workflow Guide

### Repository
`https://github.com/colab26/data_leakage_in_llm.git`

---

### Step 1 — Fork the repository

Each collaborator goes to the repo page on GitHub and clicks the **Fork** button (top right). This creates a personal copy under their own GitHub account, e.g.:

```
https://github.com/<their-username>/data_leakage_in_llm.git
```

---

### Step 2 — Clone their fork locally

```bash
git clone https://github.com/<their-username>/data_leakage_in_llm.git
cd data_leakage_in_llm
```

---

### Step 3 — Add the original repo as upstream remote

This lets them pull the latest changes from the main repo later.

```bash
git remote add upstream https://github.com/colab26/data_leakage_in_llm.git
```

Verify remotes:

```bash
git remote -v
```

They should see:

```
origin    https://github.com/<their-username>/data_leakage_in_llm.git (fetch)
origin    https://github.com/<their-username>/data_leakage_in_llm.git (push)
upstream  https://github.com/colab26/data_leakage_in_llm.git (fetch)
upstream  https://github.com/colab26/data_leakage_in_llm.git (push)
```

---

### Step 4 — Create a new branch for their work

**Never work directly on `main`.** Always create a feature branch:

```bash
git checkout -b feature/descriptive-branch-name
```

Example:

```bash
git checkout -b feature/add-data-preprocessing
```

---

### Step 5 — Make changes and commit

```bash
# Make edits to files...

git add .
git status          # Review what's staged
git commit -m "Add data preprocessing pipeline"
```

For multiple commits, keep them focused — one logical change per commit.

---

### Step 6 — Push the branch to their fork

```bash
git push origin feature/descriptive-branch-name
```

---

### Step 7 — Create a Pull Request (PR)

1. Go to their fork on GitHub: `https://github.com/<their-username>/data_leakage_in_llm`
2. GitHub will show a banner: **"Compare & pull request"** — click it
3. Make sure the PR targets:
   - **Base repository:** `colab26/data_leakage_in_llm` → **base:** `develop`
   - **Head repository:** `<their-username>/data_leakage_in_llm` → **compare:** `feature/descriptive-branch-name`
4. Write a clear title and description of what was changed and why
5. Click **Create pull request**

---

### Step 8 — Review and merge (repo owner: baijaw@umich.edu)

1. Go to the repo's **Pull requests** tab
2. Click on the PR
3. Review the changes in the **Files changed** tab
4. Leave comments or request changes if needed
5. When satisfied, click **Approve** then **Merge pull request**
6. Choose **"Create a merge commit"** (recommended for clean history)
7. Click **Confirm merge**
8. Optionally delete the feature branch on GitHub after merging

---

### Step 9 — Collaborators sync their fork after a merge

After any PR is merged into `colab26/develop`, each collaborator should update their local copy:

```bash
git checkout develop
git fetch upstream
git merge upstream/develop
git push origin develop
```

This keeps their fork's `main` in sync with the original repo before starting new work.

---

### Quick Reference Card

| Action | Command |
|--------|---------|
| Clone fork | `git clone https://github.com/<you>/data_leakage_in_llm.git` |
| Add upstream | `git remote add upstream https://github.com/colab26/data_leakage_in_llm.git` |
| New branch | `git checkout -b feature/my-change` |
| Stage & commit | `git add .` then `git commit -m "message"` |
| Push branch | `git push origin feature/my-change` |
| Sync after merge | `git fetch upstream && git merge upstream/develop && git push origin develop` |

---

### Rules for the team

1. **Never push directly to `main`** — always use feature branches and PRs
2. **Always sync before starting new work** (Step 9)
3. **One feature per branch** — keep PRs focused and reviewable
4. **Write descriptive commit messages** — future you will thank present you
