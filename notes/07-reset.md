# Reset

## What Is Git Reset?

`git reset` is used to move the current branch pointer to another commit.

It can also affect the staging area and working tree depending on the reset mode used. 

The three main modes are:
- `git reset --soft`
- `git reset --mixed`
- `git reset --hard`

---

## Reset Modes Summary

|Mode|Branch Pointer|Staging Area|Working Tree|
|---|---|---|---|
|`--soft`|Moves|Keeps changes staged|Keeps changes|
|`--mixed`|Moves|Unstages changes|Keep changes|
|`--hard`|Moves|Removes changes|Removes changes|

---

## Starting Example

Current history:
```
Commit A
   │
Commit B
   │
Commit C ← HEAD
```

You want to undo `Commit C`.

---

### Soft Reset

Command:
```bash
git reset --soft HEAD~1
```

Result
```
Commit A
   │
Commit B ← HEAD
```

The changes from `Commit C` are still staged.

Use this when you want to undo the commit but keep the changes ready to recommit.

Example use case:
```
You committed with the wrong message and want to recommit properly.
```

Then:
```bash
git commit -m "Better commit message"
```

---

### Mixed Reset

Command:
```bash
git reset --mixed HEAD~1

# Or

git reset HEAD~1
```

Result:
```
Commit A
   │
Commit B ← HEAD
```

The changes from `Commit C` are kept in the working tree but removed from staging.

Use this when you want to undo the commit and decide again what to stage.

Example use case:
```
You accidentally committed too many files and want to separate them into smaller commits.
```

Then:
```bash
git add file1.txt
git commit -m "Commit file1 only"
```

---

### Hard Reset

Command: 
```bash
git reset --hard HEAD~1
```

Result:
```
Commit A
   │
Commit B ← HEAD
```

The changes from `Commit C` are removed from both staging area and working tree.

Use this when you want to completely discard the commit and its changes.

WARNING: **This can permanently remove uncommitted work.**

---

## Reset to a Specific Commit

View history:
```bash
git log --oneline
```

Example:
```
a1b2c3d Add error handling
b2c3d4e Add logging
c3d4e5f Initial backup script
```

Reset to a specific commit:
```bash
git reset --mixed b2c3d4e
```

This moves HEAD back to that commit.

---

## Unstage a File

`git reset` can also unstage files.

Example:
```bash
git add notes.txt
```

Unstage:
```bash
git reset notes.txt
```

Modern alternative:
```bash
git restore --staged notes.txt
```

Both remove the file from the staging area but keep the working tree changes.

---

## Reset vs Restore

|Command|Main Purpose|
|---|---|
|`git reset`|Move branch pointer or unstage changes|
|`git restore`|Restore file contents or unstage files|
|`git revert`|Create a new commit that undoes another commit|

---


