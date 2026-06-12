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

Pull Request Example

```YAML
name: PR Validation

on: pull_request

jobs:
  validate:
    runs-on: ubuntu-latest

    steps:
      - run: echo "Validating pull request"
```

