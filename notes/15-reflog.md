# Reflog

## What is Reflog?

Reflog stands for `Reference Log`.

Git records changes to `HEAD`, `Branches` everytime you `Commit`, `Reset`, `Rebase`, `Merge`, `Switch Branches`. 

Git records the action in the reflog.

---

## Why Reflog matters

Suppose you accidentally run:
```bash
git reset --hard HEAD~3
```

History:
```
Commit A
Commit B
Commit C
Commit D ← HEAD
```

After reset:
```
Commit A ← HEAD
```

Looks like:
```
Commit B
Commit C
Commit D
```
are gone.

But Git still remembers them.

Reflog can find them.

---

## Reflog vs Log

### Git Log

Shows commit history.
```bash
git log --oneline
```

---

### Git Reflog

Shows HEAD movement history.
```bash
git reflog
```

Example:
```
HEAD@{0}: reset: moving to HEAD~1
HEAD@{1}: commit: Add logging
HEAD@{2}: commit: Initial commit
```

---

## Viewing Reflog

Basic command:
```bash
git reflog
```

Example output:
```
a1b2c3d HEAD@{0}: commit: Add monitoring
b2c3d4e HEAD@{1}: reset: moving to HEAD~1
c3d4e5f HEAD@{2}: commit: Add logging
```

Each entry records:
```
Commit
Action
Position
```

---

## Understanding HEAD References

Example:
```
HEAD@{0} # current position

HEAD@{1} # previous position

HEAD@{2} # position before that
```

Visualization:
```
Newest
 │
 ▼
HEAD@{0}
HEAD@{1}
HEAD@{2}
HEAD@{3}
```

---

## Recovering From Hard Reset

History:
```
Commit A
Commit B
Commit C
Commit D ← HEAD
```

Mistake:
```bash
git reset --hard HEAD~3
```

Result:
```
Commit A ← HEAD
```

Find old commit:
```bash
git reflog
```

Output:
```
HEAD@{1}: commit: Commit D
```

Restore:
```bash
git reset --hard HEAD@{1}

# or 

git reset --hard a1b2c3d
```
Commit D returns.

---

## Recover Deleted Branches

Before deletion:
```
feature-monitoring
 │
 ▼
Commit D
```

Delete branch:
```bash
git branch -D feature-monitoring
```

Oops.

Check reflog:
```bash
git reflog
```

Find commit:
```
a1b2c3d HEAD@{5}: commit: Add monitoring
```

Recreate branch:
```bash
git branch feature-monitoring a1b2c3d
```

Branch restored.

---

## Recovering From Bad Rebase

Before:
```
Commit A
Commit B
Commit C
```

Run:
```bash
git rebase main
```

Result:
```
History becomes messy
```

Check reflog:
```bash
git reflog
```

Find pre-rebase position:
```
HEAD@{4}: rebase (start)
```

Return:
```bash
git reset --hard HEAD@{4}
```

Repository restored.

---

## Reflog and Detached HEAD

Checkout old commit:
```bash
git checkout a1b2c3d
```

Detached HEAD.

Forget where you came from.

Find previous branch:
```bash
git reflog
```

Example:
```
HEAD@{1}: checkout: moving from main to a1b2c3d
```

You can return safely.

---

## Useful Commands

```bash
git reflog                      # view reflog
git reflog show main            # view branch reflog
git reset --hard HEAD@{3}       # restore using reflog reference
git branch recovery HEAD@{3}    # create recovery branch
```

---
