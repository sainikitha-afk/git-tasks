# Task 8: Using Git Hooks for Automated Checks

## Objective

The objective of this task is to understand how to use Git hooks to run automated checks before a commit is finalized, ensuring that only valid changes are committed to the repository.

---

## Steps Performed

### 1. Initial Setup

A file named `app.js` was created and committed to the repository.

```bash
git add app.js
git commit -m "Initial commit for hooks demo"
```

---

### 2. Creating a Pre-Commit Hook

A pre-commit hook was created inside the `.git/hooks` directory.

```bash
cd .git/hooks
notepad pre-commit
```

A script was added to run checks before every commit.

---

### 3. Writing the Hook Script

The script checks whether the file contains the word "error". If found, the commit is blocked.

```bash
#!/bin/sh

echo "Running pre-commit checks..."

if grep -i "error" task-8/app.js
then
  echo "Commit blocked: Found the word 'error' in app.js"
  exit 1
fi

echo "All checks passed. Proceeding with commit."
exit 0
```

---

### 4. Testing the Hook

A change containing the word "error" was added to the file and an attempt was made to commit.

```bash
git add app.js
git commit -m "Test hook"
```

The hook executed before the commit and checked the file content.

---

### 5. Successful Commit

After removing the issue from the file, the commit was attempted again and completed successfully.

---

## Output Explanation

The terminal output demonstrates:

* The pre-commit hook runs automatically before each commit
* The script checks the file content for specific conditions
* If the condition fails, the commit is prevented
* If the condition passes, the commit proceeds normally

---

## Key Concepts

* Git hooks for automation
* Pre-commit checks
* Preventing invalid commits
* Improving development workflow

---

## How Git Hooks Improve Code Quality

Git hooks allow developers to enforce rules before code is committed. This helps in:

* Preventing errors from entering the repository
* Maintaining consistent coding standards
* Automating repetitive checks such as linting or testing
* Improving collaboration in team environments

---

## Conclusion

Git hooks provide a way to automate checks and enforce quality standards during development. By using a pre-commit hook, it is possible to ensure that only valid and clean code is committed to the repository.
