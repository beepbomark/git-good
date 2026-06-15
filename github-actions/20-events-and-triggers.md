# Events and Triggers

## What Is an Event?

An event is an activity that occurs inside a GitHub repository.

Examples:
```
Push
Pull Request
Tag Creation
Issue Creation
Manual Trigger
```

GitHub Actions listens for these events.

When an event occurs:
```
Event
  │
  ▼
Workflow Triggered
```

---

## Why Events Matter

Without triggers, `Workflow` never runs.

The trigger determines `When`, `Where`, and `Why` a workflow executes.

---

## The on Keyword

Triggers are defined using:
```YAML
on:
```

Example:
```YAML
on: push
```

Meaning:
```
Run workflow when a push occurs.
```

---

## Push Event

### Basic Push Trigger

```YAML
on: push
```

Meaning:
```
Any push
     │
     ▼
Workflow Runs
```

---

### Push Example

```YAML
name: Push Demo

on: push

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Push detected"
```

---

## Pull Request Event

### Basic Pull Request Trigger

```YAML
on: pull_request
```

---

### Visualization

```
Feature Branch
      │
      ▼
Pull Request
      │
      ▼
Workflow Runs
```

---

### Pull Request Example

```YAML
name: PR Validation

on: pull_request

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Validating pull request"
```

## Workflow Dispatch

### Manual Trigger

```YAML
on:
  workflow_dispatch:
```

Meaning:
```
GitHub UI
     │
Run Workflow
     │
     ▼
Workflow Executes
```

### Example

```
name: Manual Workflow

on:
  workflow_dispatch

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Manual workflow started"
```

---

### Why Workflow Dispatch is Useful

Examples:
- Run Backup
- Generate Report
- Deploy Application
- Execute Maintenance Tasks

without requiring a push

---

## Multiple Triggers

A workflow can listen for multiple events.

Example:
```YAML
on:
  push:
  pull_request:
```

Meaning:
```
Push
 OR
Pull Request
```

will trigger the workflow.

---

### Visualization

```
Push
  │
  ├─────────┐
  ▼         │
Workflow ◄──┘
  ▲
  │
Pull Request
```

---

## Branch Filters

Sometimes workflows should run only on specific branches.

---

### Main Branch Only

```YAML
on:
  push:
    branches:
      - main
```

Meaning:
```
main
 │
 ▼
Workflow Runs
```

```
feature/*
 │
 ▼
Workflow Does Not Run
```

---

### Multiple Branches

```YAML
on:
  push:
    branches:
      - main
      - develop
```

Meaning:
```
main
develop
```

trigger the workflow.

---

## Branch Pattern Matching

Example:
```YAML
on:
  push:
    branches:
      - feature/*
```

Matches:
```
feature-login
feature-monitoring
feature-backup
```

---

## Tag Triggers

Workflows can run when tags are pushed.

---

### Example

```
on:
  push:
    tags:
      - 'v*'
```

Triggers:
```
v1.0
v1.1
v2.0
```

Does not trigger:
```
test-tag
backup
```

---

### Common Use Case

Release automation:
```
Tag Created
      │
      ▼
Build Release
      │
      ▼
Publish Artifact
```

---

## Path Filters

Only run workflows when specific files change.

---

### Markdown Example

```YAML
on:
  push:
    paths:
      - '**.md'
```

Meaning:
```
Markdown Changed
      │
      ▼
Workflow Runs
```

---

### Ignore Paths

Example:
```YAML
on:
  push:
    paths-ignore:
      - '*.txt'
```

Meaning:
```
TXT Files Changed
      │
      ▼
Workflow Ignored
```

---

## Scheduled Workflows

Run automatically on a schedule.

---

### Example
```yaml
on:
  schedule:
    - cron: '0 0 * * *'
```

Meaning:
```
Every Day
00:00 UTC
```

---

