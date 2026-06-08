# Restore

## What Is Git Restore?

`git restore` restores files to a previous state.

It can be used to:
- Discard working tree changes
- Unstage files
- Restore files from a specific commit

Unlike `git reset`, `git restore` focuses on files rather than commit history.

---

## Restore Working Tree Changes

Example:

Modify:
```
notes.txt
```

Check status:
```bash
git status
```

Output:
```
modified: notes.txt
```

Discard changes:
```bash
git restore notes.txt
```

Result:
```
notes.txt returns to the last committed version
```

---

## Restore Multiple Files

Restore all modified files:
```bash
git restore .   # This discards all uncommitted working tree changes.
```

---

## Unstage Files

Example:
```bash
git add notes.txt
```

Status:
```
Changes to be committed:
    notes.txt
```

Remove from staging:
```bash
git restore --staged notes.txt
```

Result:
```
Changes not staged for commit:
    notes.txt
```

The file remains modified but is no longer staged.

---

## Restore Both Staging and Working Tree

Suppose:
```bash
git add notes.txt
```

and you want to completely discard the changes.

```bash
# Step 1
git restore --staged notes.txt

# Step 2
git restore notes.txt

# Result: All changes removed
```

---

## Restore From a Specific Commit

View history:
```bash
git log --oneline
```

Example:
```
a1b2c3d Add logging
b2c3d4e Initial version
```

Restore file from an older commit:
```bash
git restore --source=b2c3d4e notes.txt
```

Git copies the file from that commit into the working tree.

---

## Restore vs Reset

|Command|Main Purpose|
|---|---|
|`git restore`|Restore files|
|`git reset`|Move commits or unstage changes|
|`git revert`|Undo a commit with a new commit|

---

## Useful Restore Commands

```bash
git reset file.txt                              # Restore files
git restore .                                   # Restore all files
git restore --staged file.txt                   # Unstage file
git restore --source=<commit_hash> file.txt     # Restore from specific commit
```

---

