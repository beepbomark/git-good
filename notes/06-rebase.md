# Rebase

## What Is Rebase?

Rebase takes commits from one branch and replays them on top of another branch.

Unlike merge, rebase rewrites commit history.

This creates a more linear project history.

---

## Why Rebase Matters

While working on `feature`, new commits are added to `main`.

Before merging, you may want the feature branch to start from the latest version of `main`.

This is where rebase helps.

---

## Basic Rebase Workflow

Update feature branch with latest main:
```bash
git switch feature
git rebase main
```

Then:
```bash
git switch main
git merge feature
```

Often results in a fast-forward merge.

---

## Useful Rebase Commands

```bash
git rebase main                     # start rebase
git rebase --continue               # continue after conflict
git rebase --abort                  # abort
git log --graph --oneline --all     # view history
```

---

## Interactive Rebase

Interactive rebase allows editing commit history.

```bash
git rebase -i HEAD~3

# Possible actions:
pick
reword
squash 
drop
```

---

## When to Use Rebase

Good use cases:
- Update feature branch from latest main
- Clean up local commit history
- Squash small commits
- Prepare pull requests

---

## When Not to Use Rebase

Avoid rebasing commits that have already been shared with others.

History changes for everyone.

---


