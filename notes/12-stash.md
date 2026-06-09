# Stash

## What Is Git Stash?

Git stash temporarily stores changes that have not yet been committed.

Think of it as a temporary shelf where you can place work on the shelf, switch tasks, and later retrieve it.

---

## Why Stash Matters

Imagine you are halfway through a change, suddenly you need to switch branches immediately.

Instead of creating a temporary commit, you can stash the changes.

---

## Visual Overview

Before stash:
```
Working Tree
 ├── modified file1
 ├── modified file2
 └── modified file3
```

Command:
```bash
git stash
```

After stash:
```
Working Tree
 └── clean

Stash Stack
 └── Saved Changes
```

---

## Creating a Stash

```bash
# Save current changes
git stash

# or 
git stash push

# verify
git status
```

---

## Viewing Stashes

List saved stashes:
```bash
git stash list
```

---

## Applying a Stash

Apply latest stash:
```bash
git stash apply
```

---

Applying Specific Stash
```bash
# view list
git stash list

# apply
git stash apply stash@{1}
```

---

## Pop a Stash

```bash
# Apply and remove
git stash pop
```

---

## Named Stashes

Create a descriptive stash:
```bash
git stash push -m "moniotring dashboard changes"
```

View:
```bash
git stash list
```

Example:
```
stash@{0}: monitoring dashboard changes
```

Useful when managing multiple stashes.

---

## Including Untracked Files

By default:
```bash
git stash
```
does NOT stash untracked files.

Include untracked files:
```bash
git stash -u

# or
git stash --include-untracked
```

---

## Viewing Stash Contents

```bash
# show summary:
git stash show

# detailed changes:
git stash show -p
```

---

## Deleting a Stash

```bash
# delete one stash
git stash drop stash@{0}

# delete all stashes:
git stash clear             # all stashes are removed.
```

---

## Create Branch From Stash

Sometimes a stash belongs on a new branch.

Create branch:
```bash
git stash branch feature-fix
```

Result:
```
New branch created
Stash applied
```

Useful for abandoned work that later becomes important.

---

## Useful Commands
```bash
git stash                       # create stash
git stash push -m "message"     # named stash
git stash list                  # list stashes
git stash apply                 # apply stash
git stash pop                   # apply and remove
git stash drop stash@{0}        # delete stash
git stash clear                 # clear all
```

---

