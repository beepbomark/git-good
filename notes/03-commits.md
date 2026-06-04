# Commits

## What is a Commit?

A commit is a snapshot of your project at a specific point in time.

When you create a commit, Git records:

- Current state of tracked files
- Author information
- Timestamp
- Commit message
- Reference to previous commit

A commit becomes part of the repository history.

---

## Why Commits Matter

Commits allow you to:
* Save project progress
* Track changes over time
* Recover previous versions
* Understand what changed
* Collaborate safely

---

## Commit Chain

Each commit points to its parent commit.

Commit A -> Commit B -> Commit C

Together they form a commit history chain.

Git can traverse this chain to show:
- History
- Differences
- Branches
- Merges

---

## Anatomy of a Commit

|Component|Purpose|
|---|---|
|Hash|Unique commit identifier|
|Author|Person who created commit|
|Date|Creation timestamp|
|Message|Description of change|
|Snapshot|State of project|

---

## HEAD

HEAD represents your current position in Git history.

Most Git commands operate relative to HEAD.

```bash
git show HEAD
git diff HEAD~1
```

---

## Creating a Commit

```bash
git add notes.txt
git commit -m "Add notes file"
```

---

## Viewing Commit History

```bash
git log
git log --oneline
git log --graph --oneline
```

---

## Inspecting a Commit

```bash
git show                # show contents of a commit
git show <a1b2c3d>      # specific commit
```

---

## Comparing Commits

```bash
git diff                    # view changes
git diff HEAD~1             # compare with previous commit
git diff a1b2c3d b2c3d4e    # compare two commits
```

---

