# Git Hooks

## What Are Git Hooks?

Git hooks are scripts that Git automatically executes when specific events occur.

Examples:
```
Commit Created
Push Started
Merge Completed
```
Git can run a custom script before or after these actions.

---

## Why Hooks Matter

Hooks help automate tasks such as:
- Code validation
- Linting
- Running tests
- Enforcing commit message standards
- Security checks
- Deployment automation

Without hooks:
```
Developer
 ├── Forgets tests
 ├── Bad commit messages
 └── Commits secrets
```

With hooks:
```
Git Hook
 ├── Validate
 ├── Check
 └── Allow / Reject
```

---

## Where Hooks Are Stored

Hooks are located inside `.git/hooks/`.

Example:
```
project/
└── .git/
    └── hooks/
```

View available hooks:
```bash
ls .git/hooks
```

Example output:
```
applypatch-msg.sample
commit-msg.sample
pre-commit.sample
pre-push.sample
post-merge.sample
```

---

## Hook Types

Git provides many hooks.

Common examples:

|Hook|Trigger|
|---|---|
|pre-commit|Before commit|
|commit-msg|Validate commit message|
|post-commit|After commit|
|pre-push|Before push|
|post-merge|After merge|

---

### Pre-Commit Hook

Runs before:
```bash
git commit
```

Example:
```
Developer
     │
git commit
     │
     ▼
pre-commit
     │
     ▼
Commit Created
```

Common use:
```
Run tests
Check formatting
Check syntax
```

---

#### Example Pre-Commit Hook

Create:
```
.git/hooks/pre-commit
```

Example script:
```bash
#!/bin/bash

echo "Running pre-commit checks..."

exit 0
```

Make executable:
```bash
chmod +x .git/hooks/pre-commit
```

Now every commit triggers the hook.

---

#### Rejecting a Commit

Example:
```bash
#!/bin/bash

echo "Commit rejected"
exit 1
```

Result:
```
Commit blocked
```

Important:
```
exit 0 = success
exit 1 = failure
```

---

### Commit Message Hook

Runs when a commit message is supplied.

Hook:
```
.git/hooks/commit-msg
```

Example:
```bash
#!/bin/bash

grep -qE "^[A-Z]" "$1"

if [ $? -ne 0 ]; then
    echo "Commit message must start with a capital letter"
    exit 1
fi
```

Valid:
```
Add backup script
```

Invalid:
```
add backup script
```

---

### Pre-Push Hook

Runs before:
```bash
git push
```

Example:
```
Developer
     │
git push
     │
     ▼
pre-push
     │
     ▼
Remote Repository
```

Common use:
```
Run tests
Check branch naming
Prevent force pushes
```

---

#### Example Secret Detection Hook

Simple example:
```bash
#!/bin/bash

if grep -R "PASSWORD=" .; then
    echo "Potential secret detected"
    exit 1
fi
```

Result:
```
Push blocked
```
until issue is fixed

---

### Post-Merge Hook

Runs after:
```bash
git merge
```

Common use:
```
Install dependencies
Update configuration
Refresh generated files
```

---

## Shared Hook Problem

Hooks live inside `.git/hooks`. The `.git` directory is not committed.

As a result, hooks are local only. Other developers do not automatically receive them.

---

### Common Solution

Store hook scripts:
```
project/
└── hooks/
```

Example:
```
hooks/
├── pre-commit
├── pre-push
└── commit-msg
```

---

## Useful Commands

```bash
ls .git/hooks                   # view hooks
chmod +x .git/hooks/pre-commit  # make hook executable
vim .git/hooks/pre-commit       # edit hook
```

---