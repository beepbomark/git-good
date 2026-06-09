# Cherry Pick

## What Is Cherry Pick?

`git cherry-pick` copies a specific commit from one branch and applies it onto the current branch.

It is useful when you want one commit without merging the entire branch.

Example:
```
main
 │
 ▼
Commit C

feature
 │
 ▼
Commit E
 │
Commit D
 │
Commit C
```

If you only want `Commit D` from `feature`, you can cherry-pick it into `main`.

---

## Why Cherry Pick Matters

Cherry pick is useful when:
- You need one bug fix from another branch
- You do not want to merge the full feature branch
- A commit was made on the wrong branch
- You need to backport a fix to an older release branch

---

## Basic Cherry Pick Workflow

Step 1: Find the commit hash
```bash

git log --oneline
```

Example:
```
a1b2c3d Add email alert fix
b2c3d4e Update README
c3d4e5f Initial commit
```

Step 2: Switchh to the branch that should receive the commit.
```bash
git switch main
```

Step 3: Cherry-pick the commit.
```bash
git cherry-pick a1b2c3d
```

Result:
```
The changes from commit a1b2c3d are applied to main as a new commit.
```

---

## Cherry Pick From Wrong Branch Commit

Scenario:

You accidentally committed a fix on the wrong branch.

```
feature-login
 │
 ▼
Commit D  ← bug fix committed here by mistake

main
 │
 ▼
Commit C
```

Fix:
```bash
git switch main
git cherry-pick Commit D
```

Now:
```
main
 │
 ▼
Commit D'
 │
Commit C
```

---

## Cherry Pick Multiple Commits

Cherry-pick commits one by one:
```bash
git cherry-pick a1b2c3d
git cherry-pick b2c3d4e
```

Or multiple commits in one command:
```bash
git cherry-pick a1b2c3d b2c3d4e
```

---

## Cherry Pick a Range of Commits

Cherry-pick a range:
```bash
git cherry-pick A..D
```

Meaning:
```
Apply commits after A up to D.
```

Applies:
```
B
C
D
```

If you want to include A as well:
```bash
git cherry-pick A^..D
```

---

## Cherry Pick Without Auto Commit

```bash
# Apply changes but do not create a commit immediately:
git cherry-pick --no-commit a1b2c3d

# or

git cherry-pick -n a1b2c3d  
```
Use this when you want to review or combine changes before committing.

Then commit manually:
```bash
git commit -m "Apply selected bug fix"
```

---

## Cherry Pick Conflicts

Conflicts can happen if the selected commit changes lines that are different in the current branch.

Start cherry-pick:
```bash
git cherry-pick a1b2c3d
```

Conflict occurs:
```
CONFLICT (content)
```
Resolve the file manually.

Then stage:
```bash
git add file.txt
```

Continue:
```bash
git cherry-pick --continue
```

---

## Abort Cherry Pick

Cancel the cherry-pick operation:
```bash
git cherry-pick --abort
```
This returns the repository to the state before cherry-pick started.

---

## Cherry Pick vs Merge

|Command|Purpose|
|---|---|
|`git merge`|Bring an entire branch into current branch|
|`git cherry-pick`|Bring selected commit only|

Example:
- Use merge when you want the full branch.
- Use cherry-pick when you want one specific commit.

---




