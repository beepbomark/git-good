# Workflow Syntax

## Why Workflow Syntax Matters

GitHub Actions workflows are written in YAML.

The syntax controls:
- When workflows run
- What jobs are created
- What steps are executed
- What actions are used
- What conditions are applied

A small indentation or syntax mistake can cause the workflow to fail.

---

## Basic Workflow Structure

```YAML
name: Demo Workflow

on: push

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - name: Print message
        run: echo "Hello GitHub Actions"
```

Basic structure:
```
Workflow
 ├── name
 ├── on
 └── jobs
      └── job-name
           ├── runs-on
           └── steps
```

---

### name

Defines a readable name for the workflow.
```YAML
name: Demo Workflow
```

This appears in:
```
GitHub Repository
└── Actions Tab
```

---

### jobs

Define work to be performed.

```YAML
jobs:
  demo:
```

In this example:
```
demo
```
is the job name.

A workflow can contain one or more jobs.

---

### runs-on

Defines the runner machine.

```YAML
runs-on: ubuntu-latest
```

This means the job runs on a GitHub-hosted Ubuntu runner.

---

### steps

Defines the tasks inside a job.

```YAML
steps:
  - name: Print message
    run: echo "Hello"
```
Steps run from top to bottom.

---

### name in Steps

A step can also have a name.

```YAML
steps:
  - name: Print message
    run: echo "Hello"
```

This makes workflow logs easier to read.

---

### run

`run` executes shell commands on the runner.

Example:
```YAML
- name: Show current directory
  run: pwd
```

Multiple commands:
```YAML
- name: Show system information
  run: |
    uname -a
    pwd
    ls -la
```

The `|` allows multiple shell commands.

---

### uses

`uses` runs an existing action.

Example:
```YAML
- name: Checkout repository
  uses: actions/checkout@v4
```

Meaning:
```
Use the checkout action version 4.
```

This downloads your repository onto the runner.

---

### run vs uses

|Syntax|Purpose|
|---|---|
|`run`|Run shell commands|
|`uses`|Run an existing action|

Example:
```YAML
steps:
  - name: Checkout repository
    uses: actions/checkout@v4

  - name: List files
    run: ls -la
```

---

### with

`with` passes input values to an action.

Example:
```YAML
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: "3.12"
```

Meaning:
```
Use Python version 3.12.
```

`with` is usually used together with `uses`.

---

### env

`env` defines environment variables.

Workflow-level example:
```YAML
env:
  APP_NAME: git-good
```

Use inside a step:
```
- name: Print app name
  run: echo $APP_NAME
```

---

### Job-Level Environment Variables

```YAML
jobs:
  demo:
    runs-on: ubuntu-latest

    env:
      APP_NAME: git-good

    steps:
      - name: Print app name
        run: echo $APP_NAME
```

The variable is available to all steps inside the job.

---

### Step-Level Environment Variables

```YAML
steps:
  - name: Print message
    env:
      MESSAGE: Hello
    run: echo $MESSAGE
```

The variable is available only inside that step.

---

### if

`if` controls whether a step or job should run.

Example:
```YAML
- name: Run only on main
  if: github.ref == 'refs/heads/main'
  run: echo "Running on main branch"
```

Meaning:
```
This step only runs when the branch is main.
```

---

### needs

`needs` makes on job depend on another job.

Example:
```YAML
jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - run: echo "Linting"

  test:
    needs: lint
    runs-on: ubuntu-latest
    steps:
      - run: echo "Testing"
```

Visualization:
```
lint
  │
  ▼
test
```

---

### Complete Example

```YAML
name: Syntax Demo

on: push

env:
  APP_NAME: git-good

jobs:
  demo:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Show repository files
        run: ls -la

      - name: Print app name
        run: echo $APP_NAME
```

---

### Multi-Job Example

```YAML
name: Multi Job Demo

on: push

jobs:
  lint:
    runs-on: ubuntu-latest

    steps:
      - name: Run lint placeholder
        run: echo "Linting files"

  test:
    needs: lint
    runs-on: ubuntu-latest

    steps:
      - name: Run test placeholder
        run: echo "Running tests"
```

---

