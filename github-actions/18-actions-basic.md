# GitHub Actions Basics

## What Is GitHub Actions?

GitHub Actions is GitHub's automation platform.

It allows tasks to be executed automatically when specific events occur in a repository.

Examples:
- Run tests
- Validate code
- Build applications
- Generate reports
- Deploy software

GitHub Actions is commonly used for:
```
CI/CD
Automation
Validation
Deployment
```

---

## Why GitHub Actions Matters

Without automation:
```
Developer
    │
    ├── Run Tests
    ├── Check Formatting
    ├── Validate Code
    └── Deploy Application
```

Everything is performed manually.

With GitHub Actions:
```
Developer
    │
git push
    ▼
GitHub Actions
    │
    ├── Run Tests
    ├── Validate Files
    ├── Build Project
    └── Deploy
```

Tasks run automatically.

---

## Git vs GitHub Actions

Git: Version Control

Examples:
```bash
git commit
git branch
git merge
git rebase
```

GitHub Actions: Automation Platform

Examples:
```
Run Tests
Lint Code
Build Artifacts
Deploy Applications
```

Relationship:
```
Git
 │
 git push
 ▼
GitHub
 │
 ▼
GitHub Actions
```

---

## Workflow Components

Every workflow contains several core components.

```YAML
name:
on:
jobs:
runs-on:
steps:
```

---

### name

Defines the workflow name.

Example:
```YAML
name: Hello Workflow
```

Appears in:
```
GitHub
└── Actions Tab
```

---

### on

Defines when the workflow should run.

Example:
```YAML
on: push
```

Meaning:
```
Push
  │
  ▼
Workflow Runs
```

Common triggers:
```YAML
on: push

on: pull_request

on: workflow_dispatch
```

---

### jobs

A workflow contains one or more jobs.

Example:
```YAML
jobs:
```

Visualization:
```
Workflow
 │
 ├── Job A
 ├── Job B
 └── Job C
```

Each job runs independently.

---

### runs-on

Defines the machine used to execute a job.

Example:
```YAML
runs-on: ubuntu-latest
```

GitHub creates a temporary virtual machine:
```
Ubuntu VM
```

Common runners:
```
ubuntu-latest
windows-latest
macos-latest
```

---

### steps

Steps define the actions performed by a job.

Example:
```YAML
steps:
```

Visualization:
```
Job
 │
 ├── Step 1
 ├── Step 2
 └── Step 3
```

Steps execute sequentially.

---

## Workflow Lifecycle

The most important GitHub Actions diagram:
```
Developer
    │
git push
    ▼
GitHub Repository
    │
Trigger Event
    ▼
Workflow
    │
Runner
    ▼
Steps
    │
Success / Failure
```

---

## First Workflow Example

Example:
```YAML
name: Hello Workflow

on: push

jobs:
  hello:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v4

      - run: echo "Hello GitHub Actions"
```

---

### Understanding actions/checkout

Almost every workflow begins with:
```YAML
- uses: actions/checkout@v4
```

Without checkout:
```
Runner
└── Empty
```

With checkout:
```
Runner
└── Repository Files
```

GitHub downloads your repository onto the runner.

---

### Understanding Run

Execute shell commands.

Example:
```YAML
- run: echo "Hello GitHub Actions"
```

Equivalent to running:
```bash
echo "Hello GitHub Actions"
```

inside the runner

---

### Workflow Location

GitHub Actions workflows are stored inside:
```
.github/workflows/
```

Example:
```
git-good/
│
├── notes/
│
└── .github/
    └── workflows/
        └── hello.yml
```

GitHub automatically detects workflows in this location.

---

### Viewing Workflow Results

After pushing:
```bash
git push
```

Open:
```
GitHub Repository
└── Actions
```

You will see:
```
Hello Workflow
```

Status:
```
✔ Success

or

✖ Failure
```

---