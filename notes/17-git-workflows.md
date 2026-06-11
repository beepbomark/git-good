# Git Workflows

## What Is a Git Workflow?


A Git workflow is a process that defines:

- How branches are created
- How changes are integrated
- How releases are managed
- How developers collaborate

Git provides the tools.

A workflow defines how those tools are used.

---

## Why Workflows Matter

Without a workflow:
```
Developer A
Developer B
Developer C
```
may all work directly on:
```
main
```
Result:
```
Conflicts
Confusion
Unstable code
```
With a workflow:
```
main
feature branches
release process
```
development becomes organized.

---

## Feature Branch Workflow

### Overview

The most common workflow.

Every feature is developed in its own branch.

Example:
```
main
 │
 ├── feature-login
 │
 ├── feature-monitoring
 │
 └── bugfix-alerts
```

---

### Workflow

Create branch:
```bash
git switch -c feature-monitoring
```

Work normally:
```bash
git add .
git commit -m "Add monitoring dashboard"
```

Merge back:
```bash
git switch main
git merge feature-monitoring
```

Delete branch:
```bash
git branch -d feature-monitoring
```

---

### Advantages

```
Simple
Easy to understand
Safe
Widely used
```

---

## Git Flow

### Overview

Git Flow uses dedicated branches for:
```
main
develop
feature/*
release/*
hotfix/*
```

---

### Structure

```
main
 │
 └── Production

develop
 │
 └── Active Development
```

Feature branches:
```
feature-login
feature-monitoring
feature-backup
```

---

### Example

```
main
 │
develop
 │
feature-monitoring
```

Workflow:
```
Feature
     │
     ▼
Develop
     │
     ▼
Release
     │
     ▼
Main
```

---

### Advantages

```
Structured
Good for large teams
Clear release process
```

---

### Disadvantages

```
Many branches
Complex
Heavy process
```

---

## Trunk-Based Development

### Overview

All developers work close to:
```
main
```
(or trunk).

Feature branches are:
```
Small
Short-lived
```

---

### Example

```
main
 │
Commit A
 │
Commit B
 │
Commit C
```

Changes are merged quickly.

---

### Advantages

```
Simple
Fast integration
Fewer merge conflicts
```

---

### Disadvantages

```
Requires discipline
Requires automated testing
```

---

## Release Workflow Using Tags

Common release process:
```
main
 │
Commit A
 │
Commit B
 │
Commit C ← v1.0
 │
Commit D
 │
Commit E ← v1.1
```

Tag release:
```bash
git tag -a v1.0 -m "Version 1.0"
```

Push:
```bash
git push origin v1.0
```

---

## Hotfix Workflow

Production bug discovered.

Current release:
```
main
 │
Commit C ← v1.0
```

Create branch:
```bash
git switch -c hotfix-login
```

Fix:
```
Commit D
```

Merge:
```bash
git switch main
git merge hotfix-login
```

Tag:
```bash
git tag -a v1.0.1 -m "Hotfix release"
```

---

## Using Rebase in Workflows

Feature branch:
```
feature-monitoring
```

Main receives updates:
```
main
 │
Commit D
 │
Commit C
```

Update feature:
```bash
git switch feature-monitoring
git rebase main
```

Result:
```
Feature now starts from latest main.
```

---

## Using Cherry-Pick in Workflows

Production branch:
```
main
```

Feature-branch:
```
feature-monitoring
```

Need only one fix:
```bash
git cherry-pick a1b2c3d
```

No need to merge the entire branch.

---

## Workflow Comparison

|Workflow|Best for|
|---|---|
|Feature Branch|Most teams|
|Git Flow|Large release-driven projects|
|Trunk-Based Development|Fast-moving teams|
|Hotfix Workflow|Production fixes|
|Release Tag Workflow|Versioned releases|

---

