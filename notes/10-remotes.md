# Remotes

## What Is a Remote?

A remote is another Git repository located somewhere else.

Common locations:
- GitHub
- GitLab
- Bitbucket
- Internal Git servers

Example:
```
Local Repository
       │
       ▼
Remote Repository
```

A remote allows repositories to exchange commits and history.

---

## Why Remotes Matter

Without remotes, only you have access to the repository.

With remotes, multiple developers can collaborate using the same repository.

---

## Local vs Remote Repository

```
Local Repository
├── Working Tree
├── Staging Area
└── Commit History


Remote Repository
└── Shared Commit History
```

Changes are not automatically synchronized.

You must explicitly:
```
Fetch 
Pull 
Push
```

---

## Common Remote Names

By convention `origin` usually refers to the primary remote repository.

Example:
```
origin
 └── github.com/user/project.git
```

---

## Viewing Remotes

View configured remotes:
```bash
git remove -v
```

Example:
```
origin https://github.com/user/project.git (fetch)
origin https://github.com/user/project.git (push)
```

---

## Adding a Remote

Create a connection to GitHub:
```bash
git remote add origin https://github.com/user/project.git
```

Verify:
```bash
git remove -v
```

---

## Understanding Fetch

Fetch downloads changes from the remote repository.
```bash
git fetch
```

Visualization:
```
Remote Repository
       │
       ▼
Download Commits
       │
       ▼
Local Repository
```

Important:
```
Fetch does NOT modify your working files.
```

It only updates remote tracking information.

---

## Understanding Pull

Pull downloads changes and updates your branch.
```bash
git pull
```

Equivalent to:
```bash
git fetch
git merge
```

Visualization:
```
Remote Repository
       │
       ▼
Fetch
       │
       ▼
Merge
       │
       ▼
Local Branch
```

---

## Understanding Push

Push uploads commits to a remote repository.
```bash
git push
```

Visualization:
```
Local Repository
       │
       ▼
Upload Commits
       │
       ▼
Remote Repository
```

---

## First Push

Push current branch:
```bash
git push -u origin main
```

Explanation:
```
origin = remote name
main   = branch name
-u     = set upstream branch
```

After this:
```bash
git push
```

is usually sufficient.

---

## Remote Tracking Branches

Git keeps references to remote branches.

Example:
```
main
```

Local branch:
```
main
```

Remote tracking branch:
```
origin/main
```

Visualization:
```
main
 │
 ▼
Commit C

origin/main
 │
 ▼
Commit B
```

This indicates your local branch is ahead.

---

## Viewing Branchs

```bash
git branch      # local branches
git branch -r   # remote branches
git branch -a   # all branches
```

---

## Changing a Remote URL

```bash
git remote -v   # view current remote
git remote set-url origin https://github.com/user/newrepo.git   # change URL
git remote -v   # verify
```

---

## Removing a Remote

```bash
git remote remove origin    # remote remote
git remote -v               # verify
```

No remotes should appear.

---

## Useful Remote Commands

```bash
git remote -v                   # view remotes
git remote add origin <url>     # add remote
git fetch                       # fetch
git pull                        # pull
git push                        # push
git push -u origin main         # push first time
```

---

