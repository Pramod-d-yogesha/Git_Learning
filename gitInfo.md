# 1. What is Git? How is it different from other version control systems?

Git is a **distributed version control system (DVCS)** that helps developers track changes in their codebase, collaborate with others, and manage project history efficiently. Unlike traditional **centralized version control systems (CVCS)**, Git allows every user to have a full copy of the repository, including its entire history, on their local machine.

This design provides more flexibility, faster performance, and better data safety.

![image](https://github.com/user-attachments/assets/6f45bb8d-42c9-48cd-bd29-ac6e81d00b3f)

## Key differences between CVCS and DVCS

| #  | Topic       | Centralized VCS (CVCS)                                      | Distributed VCS (DVCS)                                    |
|----|------------|--------------------------------------------------------------|-----------------------------------------------------------|
| 1  | Cloning    | Only specific files or folders are checked out.              | The entire repository (full history) is cloned.            |
| 2  | History    | No commit history/logs are available locally.                | Full commit history/logs are available locally.            |
| 3  | Online use | Always requires an internet connection for any operation.    | Only needs internet for pushing and pulling; commits work offline. |
| 4  | Backup     | No local backup; data loss if the central server fails.      | Local copy serves as a full backup.                        |
| 5  | Speed      | Slower because every action communicates with the server.    | Faster because most actions happen locally.                |


# 🚀 2. Git vs. GitHub: What’s the Difference?

| Aspect              | Git                                             | GitHub                                                      |
|---------------------|-------------------------------------------------|-------------------------------------------------------------|
| **Type**            | A tool (software).                              | A service (platform/website).                                |
| **What it is**      | A **distributed version control system (DVCS)** used to track code changes locally and manage project history. | A **cloud-based hosting service** that lets you store your Git repositories online and collaborate with others. |
| **Functionality**   | Lets you create repositories, track changes, branch, merge, etc., all on your local machine. | Adds features like **issue tracking, pull requests, web-based interface, team collaboration, and CI/CD integration.** |
| **Internet needed?**| Works **offline** (except when pushing/pulling to/from remotes). | Fully **online platform** (you need the internet to access it). |
| **Example tools**   | Commands like `git init`, `git commit`, `git push`. | Website features like forks, stars, GitHub Actions, and the GitHub web editor. |
| **Ownership**       | Open-source (created by Linus Torvalds).        | Owned by Microsoft.                                          |
| **Where it runs**   | On your **local machine** (CLI or GUI clients). | On the **web/cloud** (access via browser or API).            |

---

## 🔑 In simple terms:

- **Git** = The tool that **manages code history** on your computer.
- **GitHub** = A **place to store/share your Git repositories online** and collaborate with others easily.

---

## 💡 Bonus tip:

GitHub is **not the only hosting platform**—there are others like **GitLab, Bitbucket, Azure DevOps, and more**—but GitHub is the most popular globally.

 # 3. 🔍 What is a Repository in Git?

A **repository (or "repo")** in Git is like a **project folder** that **tracks your code, files, and their complete history**.

It contains:

- Your **project files** (code, docs, images, etc.).
- A **.git folder** (hidden) where **Git stores all the version control data**—like commits, branches, and tags.

## 🗂️ Types of repositories:

1️⃣ **Local repository:**

- Stored on your own computer.
- Created with `git init` or by cloning a remote repository.
- Lets you work, commit, branch, and track history offline.

2️⃣ **Remote repository:**

- Stored on a remote server (like GitHub, GitLab, Bitbucket).
- Lets you collaborate with others by pushing and pulling code.

---

## 🚦 Example:

```bash
# Create a new Git repository
git init my-project

# This creates:
# my-project/
# ├── .git/    (Git’s metadata & history)
# └── ...      (your project files)
```
# 🔄 4. Git Command Differences git clone vs. git pull and git fetch vs. git pull

## 1️⃣ git clone vs. git pull

| Aspect            | `git clone`                                                | `git pull`                                              |
|-------------------|------------------------------------------------------------|---------------------------------------------------------|
| **What it does**  | Downloads the **entire repository** (including history) from a remote and **creates a local copy.** | Downloads **new changes** from the remote and **merges** them into your current local branch. |
| **When to use**   | When you're setting up the repository **for the first time.** | When you **already have the repo cloned** and want to update it. |
| **Effect**        | Creates a **new folder** with all files + full Git history. | **Updates your existing local repo** with new changes.   |
| **Example**       | `git clone https://github.com/user/repo.git`               | `git pull origin main`                                   |

✅ **Simple terms:**

- `git clone`: 📥 **First-time setup.**
- `git pull`: 🔄 **Keep things updated.**

---

# 2️⃣ `git fetch` vs. `git pull`
![image](https://github.com/user-attachments/assets/af83e15d-b56d-4d56-ae05-0300a3640b92)
## 📌 Scenario

Imagine you're working on a project with a remote repository. Your collaborator has pushed new commits to the `main` branch on the remote repository. You want to incorporate these changes into your local repository.

---

## 📡 Using `git fetch`

```bash
git fetch origin
```

**What happens:**

- Downloads new commits from the remote repository (`origin`) to your local machine.
- Updates the remote tracking branch (`origin/main`) with the new commits.
- **Does not** merge the changes into your local `main` branch automatically.

**Your local repository state:**

- `main`: Remains unchanged.
- `origin/main`: Updated with new commits from the remote.

**Next steps:**

To integrate the fetched changes into your local `main` branch:

```bash
git merge origin/main
```

or

```bash
git rebase origin/main
```

This allows you to review changes before integrating them.

---

## 🔄 Using `git pull`

```bash
git pull origin main
```

**What happens:**

- Performs a `git fetch` to retrieve new commits from the remote `main` branch.
- Automatically merges the fetched commits into your local `main` branch.

**Your local repository state:**

- `main`: Updated with new commits from the remote.
- Working directory: Reflects the latest changes.

This command is a shortcut for:

```bash
git fetch origin
git merge origin/main
```

---

## 🧠 Summary

| Command               | Fetches Updates | Merges Automatically | Use Case                                       |
|------------------------|-----------------|----------------------|------------------------------------------------|
| `git fetch origin`     | ✅              | ❌                   | When you want to **review changes** before merging |
| `git pull origin main` | ✅              | ✅                   | When you want to **update your branch immediately** |

---

| Aspect            | `git fetch`                                                | `git pull`                                               |
|-------------------|------------------------------------------------------------|----------------------------------------------------------|
| **What it does**  | **Downloads new commits** and updates your **remote tracking branches**—but does **not merge** them into your current branch. | Does **everything `fetch` does + merges** changes into your current branch. |
| **When to use**   | When you want to **inspect remote changes first** before merging. | When you want to **download + automatically update** your branch. |
| **Effect**        | Keeps your repo up-to-date with the remote, but **no local branch change** until you merge manually. | Updates both the remote tracking branches **and your local branch.** |
| **Example**       | `git fetch origin`                                         | `git pull origin main`                                    |

✅ **Simple terms:**

- `git fetch`: 📡 **Check for updates, but don’t apply them yet.**
- `git pull`: 🔄 **Check and apply updates immediately.**


# 🔄 5. Git Workflow: Working Directory, Staging Area, and Repository

## 1. What is the **Staging Area**?

The **staging area** (also called the **index**) is like a **waiting room** for your changes before they are saved permanently in Git.

Think of Git as a 3-step workflow:

1. 🔧 You **change files** → (Working Directory)
2. 🗂️ You **stage** the ones you want to commit → (Staging Area)
3. ✅ You **commit** them to Git → (Repository)

---

## 🧾 Real-World Analogy

Imagine you're writing a report:

- 🖊 You write your notes on paper (**working directory**).
- 📋 You gather the final version of the notes to submit (**staging area**).
- 📤 You send the notes to your manager (**repository**).

The **staging area** is where you collect everything **you’re ready to submit**, but **you haven’t submitted yet**.

---

## ✅ Example

You have 3 files:  
- `file1.txt` (changed)  
- `file2.txt` (changed)  
- `file3.txt` (unchanged)

You only want to commit `file1.txt`.

```bash
git add file1.txt
```

Now:
- `file1.txt` → is in the **staging area**
- `file2.txt` → is still in the **working directory**
- `file3.txt` → is unchanged

When you commit:
```bash
git commit -m "Updated file1"
```
Only `file1.txt` gets saved in Git history.

---

## 📌 Why is it useful?

- You can **control exactly what you commit**.
- You don’t have to commit every changed file.
- You can break your work into **smaller, meaningful commits**.

---

## 2. **Working Directory (Working Tree)**

- This is where you **actually edit files** on your system.
- It reflects the **current state of your project**.
- Any changes you make (add, delete, modify files) first appear here.

📂 **Example**: You open `main.cpp` and add a new function. This change is only in the working directory for now.

---
## 3. **Repository (Local Repository)**

- This is where Git **permanently stores your project history** as a series of commits.
- When you run:
  ```bash
  git commit -m "message"
  ```
  Git takes what's in the staging area and saves it to the repository.

📂 **Example**: After staging, you run:
```bash
git commit -m "Added new function to main.cpp"
```
Now the change is saved in the local Git database.

---

## 🧠 Summary

| Area             | Purpose                                 | Command to move into it          |
|------------------|------------------------------------------|----------------------------------|
| Working Directory | Where you edit files                    | *You edit manually*              |
| Staging Area     | Prepare files for commit                | `git add filename`               |
| Repository       | Stores committed project history        | `git commit -m "message"`        |

---
# 🔄 6. Checking the Status of Your Git Repository

To check the status of your Git repository, you use the command:


### What it does:
- **Shows modified files**: Lists the files that have been changed but not yet staged.
- **Shows staged files**: Displays files that are staged and ready to be committed.
- **Shows untracked files**: Files that are in your working directory but not yet added to the repository.
- **Branch information**: Displays the current branch you're working on and any changes compared to the remote repository.

### Example Output:
```bash
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git restore <file>..." to discard changes in working directory)
modified: file1.txt

Untracked files:
(use "git add <file>..." to include in what will be committed)
file2.txt

no changes added to commit (use "git add" and/or "git commit -a")
```

### Breakdown of Output:
- **Changes not staged for commit**: Files you've modified but haven't added to the staging area.
- **Untracked files**: New files that Git hasn't yet started tracking.
- **Staged changes**: Files you've added to the staging area, ready for commit.
- **Branch info**: Indicates which branch you're currently on and whether it's up to date with the remote.

---

🧠 **Summary**

| Area              | Purpose                                  | Command to check status         |
|-------------------|------------------------------------------|---------------------------------|
| Modified Files    | Files changed but not staged             | Files listed in "Changes not staged for commit" |
| Staged Files      | Files ready to be committed              | `git add <filename>`            |
| Untracked Files   | Files not yet tracked by Git             | Listed under "Untracked files" |
| Branch Information| Shows which branch you are on and status | `git status`                    |


# 🔄 7. How Do You Add Files to the Staging Area in Git?

To add files to the **staging area** in Git (i.e., to prepare them for the next commit), you use the `git add` command.

---

## 📌 Command to Add Files to Staging

```bash
git add <filename>
```

### ✅ Examples

- Add a specific file:
  ```bash
  git add index.html
  ```

- Add multiple files:
  ```bash
  git add index.html app.js style.css
  ```

- Add all modified and untracked files in the current directory:
  ```bash
  git add .
  ```

- Add all files recursively (including deleted ones):
  ```bash
  git add -A
  ```

---

## 🧠 What Happens?

When you run `git add`, you're telling Git:

> "I'm ready to include this file (or changes) in the next snapshot (commit)."

These files are moved from the **Working Directory** ➡️ **Staging Area**.

---
# 🔄 7. How to Revert a Pushed Commit in Git

We'll use **VS Code** to visually demonstrate how the code is affected by Git commands.

Initially, we have **5 commits** pushed to the remote branch on GitHub.

---

## ✅ Step 1: Make a New Commit and Push

```bash
# Add a change
git commit -am "change number 1"

# Push the change to remote
git push origin main
```

After pushing, GitHub reflects the new commit, so now the remote branch has **6 commits**.

---

## 🧩 Two Options to Revert a Pushed Commit

### 🔁 Option 1: Use `git revert` (Recommended for Shared/Public Branches)

- **Purpose:** Creates a new commit that *reverts the changes* made by a previous commit.
- **Safe for team use**: Keeps the commit history intact.
- **Results in:** Original commit + new revert commit.

```bash
git revert HEAD
```

> A text editor will open for editing the revert commit message. Save and close it.

```bash
git push origin main
```

- GitHub now shows **7 commits**, where the last one is a reversal of the 6th commit.

---

### ⚠️ Option 2: Use `git reset` (Use for Private Branches)

- **Purpose:** Removes commits from history.
- **Only safe if you're the only one working on the branch**.
- **Requires force-pushing** to overwrite history on the remote.

```bash
# Soft reset (removes commit but keeps code unstaged)
git reset HEAD~1
```

OR

```bash
# Hard reset (removes commit and code changes)
git reset --hard HEAD~1
```

Then, force push:

```bash
git push -f origin main
```

- GitHub will now show only **5 commits**, as if the last one never happened.

---

## 🧠 Summary

| Option      | Command                        | Use Case                     | Effect                                       |
|-------------|--------------------------------|------------------------------|----------------------------------------------|
| `git revert` | `git revert HEAD`              | Shared/Public branches       | Creates new commit that undoes the last one  |
| `git reset`  | `git reset [--soft|--hard] HEAD~1` + `git push -f` | Private branches (only you) | Deletes commit from history (requires force push) |


# 🔄 Undo Last Commit in Git – `--soft` vs `--mixed` Reset

## Option 3: `git reset --soft HEAD~1`

### ✅ What it does:
- Undoes the **last commit**
- Keeps all your changes in the **staging area**
- Useful when you want to **redo the commit** (maybe change message or add files)

### 📂 Example:
```bash
git reset --soft HEAD~1
git commit -m "Updated commit message"
```

---

## Option 4 :`git reset --mixed HEAD~1`

### ✅ What it does:
- Undoes the **last commit**
- Keeps all changes in the **working directory**
- Unstages everything (so nothing is in the staging area)
- Useful when you want to **manually stage** files again

### 📂 Example:
```bash
git reset --mixed HEAD~1
# Then stage and commit again
git add file1.txt
git commit -m "New commit"
```

---

## 🧠 Visual Comparison Table

| Command                    | Removes Last Commit | Keeps Changes | In Staging Area? | Use When...                              |
|----------------------------|---------------------|---------------|------------------|------------------------------------------|
| `git reset --soft HEAD~1`  | ✅                  | ✅            | ✅               | You want to redo the last commit         |
| `git reset --mixed HEAD~1` | ✅                  | ✅            | ❌               | You want to re-select files to stage     |

---

