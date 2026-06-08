# Revert

## What Is Git Revert?

`git revert` creates a new commit that reverses the changes introduced by an earlier commit.

Unlike `git reset`, revert does not remove commits from history.

Instead, Git records a new commit that undoes the previous changes.

---

## Why Revert Matters

Consider the following history:
```
Commit A
   │
Commit B
   │
Commit C ← HEAD
```

Suppose Commit C introduced a bug.

Using revert:
```bash
git revert HEAD
```

Git creates:
```
Commit A
   │
Commit B
   │
Commit C
   │
Commit D (Revert Commit C)
```

History remains intact.

The bug is undone safely.

---

## Why Not Use Reset?

Reset:
```bash
git reset --hard HEAD~1
```

Result:
```
Commit A
   │
Commit B ← HEAD
```

Commit C disappears from branch history.

This can be dangerous if Commit C was already pushed.

---

## Revert a Specific Commit

View history:
```bash
git log --oneline
```

Example:
```
a1b2c3d Add logging
b2c3d4e Add backup script
c3d4e5f Initial commit
```

Revert logging:
```bash
git revert a1b2c3d
```

Git creates a new commit that removes the logging changes.

---

## Reverting Multiple Commits
Revert several commits individually:
```bash
git revert commit1
git revert commit2
git revert commit3
```

Each creates its own revert commit.

---

## Revert Without Auto Commit

Apply revert changes but do not create a commit:
```bash
git revert --no-commit HEAD

# or

git revert -n HEAD

# Then
git commit -m "Undo recent changes"
```

---

## Revert Conflicts

Conflicts can occur if later commits modified the same lines.

---

## Abort Revert

Cancel the operation:
```bash
git revert --abort
```

Repository returns to the state before revert stated. 

---

## Revert vs Reset
|Command|Effect|
|---|---|
|`git reset`|Moves branch pointer|
|`git restore`|Restores files|
|`git revert`|Creates undo commit|

---

