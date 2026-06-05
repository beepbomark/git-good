# Merge

## What Is Merge?

A merge brings changes from one branch into another branch.

Most commonly, changes from a feature branch are merged back into `main`.

The goal is to bring the work from `feature` into `main`.

---

## Why Merge Matters

Merge allows separate work to be combined safely.

Common use cases:
- Add completed feature work into `main`
- Bring bug fixes into production branch
- Combine work from multiple developers
- Preserve branch history

---

## Basic Merge Work flow

```bash
git switch main
git merge <feature_name>
```

Meaning:
- Switch to the branch that should receive the changes
- Then merge the other branch into it.

Important: You merge INTO your current branch.

---

## Fast-Forward Merge

A fast-forward merge happens when the target branch has no new commits of its own.

Git simply moves `main` forward.

No merge commit is created.

---

## Three-Way Merge

A three-way merge happens when both branches have new commits.

Git creates a new merge commit to combine both histories.

---

## Merge Conflict

A merge conflict happens when Git cannot automatically decide which change to keep.

|Section|Meaning|
|---|---|
|`HEAD`|Current branch|
|`=======`|Separator|
|`feature`|Incoming branch|

---

### Resolving a Merge Conflict

Step 1: Open the conflicted file.
Step 2: Choose the correct content.
Step 3: Stage the resolved file.
Step 4: Complete the merge.

Git may automatically open an editor with a merge commit message.

---

### Abort a Merge

If the merge becomes confusing, cancel it `git merge --abort`.

This returns the repository to the state before the merge started.

---

## Useful Merge Commands

```bash
git merge feature                   # merge a branch
git merge --abort                   # abort merge
git log --graph --oneline --all     # view branch history
git status                          # check current status
```

---

