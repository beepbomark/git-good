# Working Tree, Staging Area and Repository

## Git's Three Main Areas

Git manages files through three main areas:
1. Working Tree
2. Staging Area
3. Repository

### Working Tree

The Working Tree contains the files currently visible in your project directory.

This is where files are:
* Created
* Modified
* Deleted

Any changes made here are not yet tracked in a commit.

---

### Staging Area

The Staging Area (Index) is where changes are prepared before committing.

Files are moved into the staging area using `git add <file>`.

---

### Repository

The Repository stores commit history.

Files enter the repository when a commit is created `git commit -m "Update README"`.

Each commit acts as a snapshot of the project.

---

## Understanding git status

The most important Git command `git status`.

It tells you:
* What is modified
* What is staged
* What is untracked
* What is ready to commit

---

## Common Commands

```bash
git status                  # view status
git add file.txt            # stage one file
git add .                   # stage all changes
git commit -m "message"     # create commit
git log                     # view commit history
```

---