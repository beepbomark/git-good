# Branches

## What Is a Branch?

A branch is a named pointer to a commit.

Git uses branches to track different lines of development within the same repository.

The branch `main` current points to the latest commit.

As new commits are created, the branch moves forward.

---

## Why Branches Matter

Branches allow changes to be developed independently without affecting the main codebase.

Common uses:
- New features
- Bug fixes
- Testing
- Experiments

Without branches, everything becomes mixed together.

With branches, changes remain isolated until ready.

Create a new branch `git branch <feature_name>`.

---

## Switching Branches

Head follows the currently checked-out branch.

When you switch branches, HEAD moves to that branch. (`git switch <feature_name>`, `git checkout <feature_name>`)

---

## Common Branch Commands

```bash
git branch <feature_name>       # create branch

git switch -c <feature_name>    # create and switch (modern)
git switch <feature_name>       # switch branch (modern)

git checkout -b <feature_name>  # create and switch (legacy)
git checkout <feature_name>     # switch branch (legacy)
```

---

