# Git Basics

## What Is Git?

Git is a distributed version control system (VCS) used to track changes in files over time.

It allows users to:

- Track changes
- Revert changes
- Create branches
- Collaborate with others
- Maintain project history

---

## Why Git Matters

Without version control:

- Changes can be overwritten
- Previous versions are difficult to recover
- Collaboration becomes complicated

Git solves these problems by maintaining a complete history of changes.

---

## Common Git Components
|Component|Purpose|
|---|---|
|Repository|Stores project history|
|Commit|Snapshot of project state|
|Branch|Independent line of development|
|Merge|Combines branches|
|Remote|Shared repository location|

## Common Commands
```bash
git init    # initialize repository
git status  # check status
git log     # view commit history
```

---

## Initial Git Configuration

Configure your identity before making commits.

```bash
git config --global user.name "John Doe"            # set your username
git config --global user.email "john@example.com"   # set your email address
git config --list                                   # verify configuration
git config user.name                                # view a specific setting
```

---

## Configuration Levels

Git configuration can be applied at different scopes.

|Level|Scope|
|---|---|
|System|Entire system|
|Global|Current user|
|Local|Current repository|

```bash
git config --global --list      # view global configuration
git config --local --list       # view local repository configuration
```

---