# Git Ignore

## What Is .gitignore?

A `.gitignore` file tells Git which files and directories should be ignored.

Ignored files:
- Are not tracked
- Do not appear as untracked files
- Are not included in commits

Example:
```
project/
├── README.md
├── script.sh
├── .gitignore
└── app.log
```

If `app.log` exists in .gitignore, Git will ignore it.

---

## Why .gitignore Matters

Many files should not be committed.

Examples:
```
Logs
Temporary files
Build outputs
Secrets
IDE settings
Dependencies
```

Without `.gitignore`:
```
project/
├── source code
├── logs
├── cache files
├── build files
└── temporary files
```
Repository becomes cluttered.

---

## Creating a .gitignore File

Create:
```bash
touch .gitignore
```

---

## Ignoring Specific Files

Ignore:
```
app.log
```

Add:
```
app.log
```

Result: `app.log` will not be tracked.

---

## Ignore File Types

Ignore all log files:
```
*.log
```

Examples:
```
app.log
server.log
backup.log
```

All ignored.

---

## Ignoring Directories

Ignore directory:
```
logs/
```

Example:
```
project/
└── logs/
```

Everything inside:
```
logs/
├── app.log
├── server.log
└── debug.log
```
is ignored.

---

## Ignoring Build Artifacts

Example:
```
build/
dist/
target/
```

---

## Ignoring Python Files

Example:
```
__pycache__/
*.pyc
venv/
.env
```

---

## Ignoring Environment Files

Environment files often contain secrets.

Example:
```
.env
.env.production
```

Never commit:
```
API keys
Passwords
Tokens
Credentials
```

---

## Viewing Ignored Files

Check ignored files:
```bash
git status --ignored
```

---

## Important Limitation

`.gitignore` only affects untracked files.

Example:
```bash
git add app.log
git commit -m "Add log file"
```

Then:
```
*.log
```
added to `.gitignore`

Result is that Git still tracks app.log because it was already committed.

---

## Stop Tracking Existing Files

Remove from Git tracking:
```bash
git rm --cached app.log
```

Commit:
```bash
git commit -m "Stop tracking log file"
```

Now `.gitignore` takes effect.

---

## Negation Rule

Ignore all log files:
```
*.log
```

Except one:
```
!important.log
```

Example:
```
app.log
server.log
important.log
```

Only:
```
important.log
```

is tracked.

---

## Useful Commands

```bash
touch .gitignore            # create file
git status --ignored        # view ignored files
git rm --cached file.txt    # stop tracking file
```

---

