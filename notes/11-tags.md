# Tags

## What Is a Tag?

A tag is a reference that points to a specific commit.

Unlike branches, tags do not move.

Example:
```
Commit A
   │
Commit B
   │
Commit C ← v1.0
   │
Commit D
   │
Commit E ← main
```

Even if new commits are added, the tag remains attached to Commit C.

---

## Why Tags Matter

Tags are commonly used to:
- Mark releases
- Mark software versions
- Mark project milestones
- Quickly return to important commits

---

## Branches vs Tags

|Branch|Tag|
|---|---|
|Moves forward|Fixed|
|Active development|Snapshot of a release|
|Receives new commits|Never changes automatically|

---

## Lightweight Tags

Create a lightweight tag:
```bash
git tag v1.0
```

Result:
```
Commit C ← v1.0
```

Git simply creates a name pointing to the commit.

---

## Annotated Tags

Annotated tags contain additional metadata.

Create:
```bash
git tag -a v1.0 -m "Version 1.0 release"
```

Information stored:
- Tag name
- Creator
- Date
- Message

Recommended for releases.

---

## Viewing Tags

List tags:
```bash
git tag
```

---

## View Tag Information

Annotated tag:
```bash
git show v1.0
```

---

## Tagging Older Commits

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

Create tag on older commit:
```bash
git tag -a v1.0 b2c3d4e -m "Version 1.0"
```

Result:
```
Commit B ← v1.0
```

---

## Checking Out a Tag

```bash
# Move to a tagged commit:
git checkout v1.0

# or
git switch --detach v1.0
```

Result:
```
HEAD detached at v1.0
```

You are viewing the repository as it existed at that release.

---

## Detached HEAD Remainder

When checking out a tag:
```
HEAD
 │
 ▼
Commit C
```

HEAD points directly to the commit rather than a branch.

This is called a Detached HEAD state.

---

## Creating a Branch From a Tag

Example:
```bash
git switch -c hotfix-v1.0 v1.0
```

Result:
```
v1.0
 │
 ▼
Commit C
 │
Commit D ← hotfix-v1.0
```

Useful when fixing older releases.

---

## Pushing Tags

```bash
# normal push
git push    # does not push tags

# push one tag
git push origin v1.0

# push all tags
git push origin --tags
```

---

## Deleting Tags

```bash
# delete local tag
git tag -d v1.0

# delete remote tag
git push origin --delete v1.0
```

---

## Common Commands

```bash
git tag v1.0                        # create lightweight tag
git tag -a v1.0 -m "Version 1.0"    # create annotated tag
git tag                             # list tags
git show v1.0                       # show tag
git push origin v1.0                # push tag
git push origin --tags              # push all tags
```

---


