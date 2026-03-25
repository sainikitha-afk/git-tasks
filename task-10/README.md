# Task 10: Comprehensive Workflow with Forced Pushes and Recovery

## Objective

The objective of this task is to simulate an advanced Git workflow involving multiple branches, history rewriting using rebase, forced pushes, and recovery of lost commits using `git reflog`.

---

## Steps Performed

### 1. Initial Setup

A base file `project.txt` was created and committed.

```bash
git add project.txt
git commit -m "Initial project setup"
```

---

### 2. Creating Multiple Branches

Three branches were created to simulate a real-world workflow:

* Feature branch:

```bash
git checkout -b feature/login
```

* Bugfix branch:

```bash
git checkout main
git checkout -b bugfix/login-error
```

* Release branch:

```bash
git checkout main
git checkout -b release/v1.0
```

Each branch introduced separate commits representing features, bug fixes, and release preparation.

---

### 3. Creating and Cleaning Commit History

On the `feature/login` branch, multiple small commits were created:

```bash
git commit -m "fix"
git commit -m "update"
```

Interactive rebase was used to clean the history:

```bash
git rebase -i HEAD~2
```

The commits were squashed into a single meaningful commit.

---

### 4. Force Push After Rewriting History

After rewriting commit history, the branch was force pushed:

```bash
git push --force
```

This updated the remote branch with the rewritten commit history.

---

### 5. Simulating Loss of Commits

A hard reset was performed:

```bash
git reset --hard HEAD~1
```

This removed the most recent commit from the visible history.

---

### 6. Recovering Lost Commits Using reflog

The commit history was inspected using:

```bash
git reflog
```

Example output:

```
HEAD@{2}: commit: update
HEAD@{3}: commit: fix
HEAD@{0}: reset: moving to HEAD~1
```

The lost commit was identified using its hash and restored:

```bash
git reset --hard <commit-hash>
```

---

## Output Explanation

The terminal output demonstrates the complete lifecycle of advanced Git operations:

* `git log --oneline` shows commit history before and after rewriting
* `git reset --hard` removes commits from the visible history
* `git reflog` retains a record of all HEAD movements, including deleted commits
* The lost commit is recovered using its hash from the reflog

After recovery:

* The previously removed commit reappears in `git log`
* The file content is restored to the expected state
* The working directory becomes clean again

---

## Key Concepts

* Multi-branch development workflow
* Interactive rebasing for history cleanup
* Force pushing rewritten history
* Risks of using `git push --force`
* Recovery using `git reflog`

---

## Why Force Push is Risky

Force pushing rewrites commit history on the remote repository. This can:

* Remove commits that others depend on
* Cause inconsistencies in shared branches
* Lead to loss of work if not handled carefully

---

## Role of reflog in Recovery

`git reflog` acts as a safety mechanism by:

* Tracking all changes to the HEAD pointer
* Retaining references to commits even after deletion
* Allowing recovery of lost commits using their hashes

---

## Best Practices

* Avoid using `git push --force` on shared branches
* Prefer `git push --force-with-lease` for safer updates
* Use force push only on feature branches
* Communicate with team members before rewriting history
* Use `git reflog` immediately after accidental changes to recover lost work

---

## What I Learned

This task provided practical experience in handling advanced Git scenarios. It demonstrated how easily commit history can be altered and how important it is to understand recovery mechanisms such as `git reflog`.

---

## Conclusion

Advanced Git operations such as rebasing and force pushing require careful handling. Understanding how to recover lost commits ensures that mistakes can be corrected safely, making `git reflog` an essential tool in real-world development workflows.
