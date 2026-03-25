# Task 9: Working with Remote Repositories and Collaboration

## Objective

The objective of this task is to simulate a collaborative workflow using a remote repository by creating branches, pushing changes, opening a pull request, and merging updates into the main branch.

---

## Steps Performed

### 1. Initial Setup

A file named `collab.txt` was created and committed to the repository.

```bash
git add collab.txt
git commit -m "Initial commit for collaboration demo"
```

The changes were pushed to the remote repository:

```bash
git push origin main
```

---

### 2. Creating a Feature Branch

A new branch was created for development work:

```bash
git checkout -b feature/task-9
```

Changes were made and committed:

```bash
echo Feature update line >> collab.txt
git add collab.txt
git commit -m "Add feature update in task 9"
```

The branch was pushed to the remote repository:

```bash
git push -u origin feature/task-9
```

---

### 3. Creating a Pull Request

On the remote repository (GitHub):

* A pull request was created from `feature/task-9` to `main`
* A title and description were added
* The changes were reviewed using the "Files changed" section

---

### 4. Code Review and Merge

The changes were verified and then merged into the `main` branch using the pull request interface.

---

### 5. Updating Local Repository

After merging, the local repository was updated:

```bash
git checkout main
git pull origin main
```

This ensured that the local branch reflected the latest changes from the remote repository.

---

## Output Explanation

The workflow demonstrates:

* Creation of a remote repository and pushing local changes
* Use of feature branches for isolated development
* Opening and reviewing a pull request
* Merging changes into the main branch
* Synchronizing local and remote repositories

---

## Key Concepts

* Local vs remote repositories
* Feature branch workflow
* Pull requests for collaboration
* Code review before merging
* Synchronization using `git push` and `git pull`

---

## What I Learned

This task provided practical experience in managing code collaboratively using Git and a remote platform. It highlighted the importance of structured workflows, code reviews, and proper synchronization between local and remote repositories.

---

## Conclusion

Working with remote repositories enables effective collaboration in software development. Using feature branches and pull requests ensures that changes are reviewed and integrated in a controlled and organized manner.
