# Git Commands Cheat Sheet with Detailed Descriptions

## 🛠️ Basic setup & configuration

| Command                                            | Detailed description                                                                             |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------ |
| `git config --global user.name "Your Name"`        | Sets your name for all Git repositories on your system (used in commits). Example: `"John Doe"`. |
| `git config --global user.email "you@example.com"` | Sets your email globally (Git associates your commits with this).                                |
| `git config --list`                                | Displays all Git configuration settings (global, local, and system-wide).                        |

## 🛠️ Repository setup

| Command           | Detailed description                                                                                        |
| ----------------- | ----------------------------------------------------------------------------------------------------------- |
| `git init`        | Creates a new Git repository in your current directory. It makes a `.git` folder to track versions.         |
| `git clone <url>` | Downloads an existing repository from a remote URL and sets it up locally, keeping it linked to the remote. |

## 🛠️ Working with changes

| Command                    | Detailed description                                                                               |
| -------------------------- | -------------------------------------------------------------------------------------------------- |
| `git status`               | Shows the status of your working directory and staging area: what's changed, staged, or untracked. |
| `git add <file>`           | Adds the specified file(s) to the staging area (preparing for commit).                             |
| `git add .`                | Adds **all modified and new files** in the current directory (recursively) to staging.             |
| `git commit -m "message"`  | Saves the staged changes as a commit, with a commit message describing the change.                 |
| `git commit -am "message"` | Shortcut: stages & commits **only tracked files** (new files must be added with `git add` first).  |
| `git diff`                 | Shows line-by-line changes that are unstaged (working directory vs. last commit).                  |
| `git diff --staged`        | Shows the difference between **staged changes** and the last commit.                               |

## 🛠️ Branching & merging

| Command                         | Detailed description                                                       |
| ------------------------------- | -------------------------------------------------------------------------- |
| `git branch`                    | Lists all branches in your repo, and marks the current one with a `*`.     |
| `git branch <branch-name>`      | Creates a new branch (doesn’t switch to it immediately).                   |
| `git checkout <branch-name>`    | Switches to an existing branch.                                            |
| `git checkout -b <branch-name>` | **Creates and switches** to a new branch in one step.                      |
| `git merge <branch-name>`       | Merges changes from the named branch into your current branch.             |
| `git branch -d <branch-name>`   | Deletes the specified branch (safe: won’t delete if unmerged work exists). |

## 🛠️ Remote repositories

| Command                       | Detailed description                                                                         |
| ----------------------------- | -------------------------------------------------------------------------------------------- |
| `git remote -v`               | Lists remote repositories and their URLs (e.g., `origin`).                                   |
| `git remote add origin <url>` | Links your local repo to a remote (commonly named `origin`).                                 |
| `git push origin <branch>`    | Pushes your branch to the remote repository.                                                 |
| `git push -u origin <branch>` | Pushes and **sets upstream tracking** (so future `git push` knows where to push by default). |
| `git pull`                    | Fetches new changes from the remote and **merges** them into your current branch.            |
| `git fetch`                   | Downloads new changes from the remote but **does not merge** (lets you inspect first).       |

## 🛠️ Undo & reset

| Command                  | Detailed description                                                                                 |
| ------------------------ | ---------------------------------------------------------------------------------------------------- |
| `git restore <file>`     | Reverts **working directory changes** to the last commit state (undo edits).                         |
| `git checkout -- <file>` | Older version of `git restore` (same purpose: discard changes).                                      |
| `git reset HEAD <file>`  | Unstages a staged file (moves it back to the working directory as modified).                         |
| `git reset --hard HEAD`  | Resets the working directory and staging area to match the latest commit (warning: **destructive**). |
| `git revert <commit>`    | Safely undoes a commit by making a **new commit that reverses** its changes. Keeps history intact.   |

## 🛠️ Viewing history

| Command                     | Detailed description                                                     |
| --------------------------- | ------------------------------------------------------------------------ |
| `git log`                   | Shows full commit history (with hashes, authors, dates, messages).       |
| `git log --oneline`         | Compact, one-line-per-commit view.                                       |
| `git log --graph --oneline` | Visualizes branching and merging as a **graph tree.**                    |
| `git show <commit>`         | Displays detailed information (diff + metadata) about a specific commit. |

## 🛠️ Stashing

| Command          | Detailed description                                                                  |
| ---------------- | ------------------------------------------------------------------------------------- |
| `git stash`      | Temporarily saves **uncommitted changes** so you can switch branches or work cleanly. |
| `git stash pop`  | Applies the latest stash and removes it from the stash list.                          |
| `git stash list` | Lists all saved stashes.                                                              |
| `git stash drop` | Removes a stash from the list (if you don’t need it anymore).                         |

## 🛠️ Rewriting history

| Command                               | Detailed description                                                                               |
| ------------------------------------- | -------------------------------------------------------------------------------------------------- |
| `git rebase <branch>`                 | Replays your current branch’s commits **on top of another branch’s commits** (linearizes history). |
| `git rebase -i <commit>`              | Interactive rebase: lets you **edit, squash, or reorder** commits in a range.                      |
| `git cherry-pick <commit>`            | Applies a **single commit’s changes** to your current branch (useful for picking fixes).           |
| `git commit --amend -m "new message"` | Modifies the last commit (you can change the message or add more changes).                         |

## 🛠️ Tagging

| Command                         | Detailed description                                         |
| ------------------------------- | ------------------------------------------------------------ |
| `git tag`                       | Lists all tags in your repository.                           |
| `git tag <tag-name>`            | Creates a simple tag (like a bookmark) on the latest commit. |
| `git tag -a <tag> -m "message"` | Creates an **annotated tag** (includes metadata + message).  |
| `git push origin <tag>`         | Pushes a single tag to the remote.                           |
| `git push origin --tags`        | Pushes **all local tags** to the remote.                     |

## 🛠️ Collaboration & inspection

| Command            | Detailed description                                                                  |
| ------------------ | ------------------------------------------------------------------------------------- |
| `git blame <file>` | Shows who last changed each line of a file (great for debugging history).             |
| `git clean -fd`    | Deletes all **untracked files and folders** (warning: **destructive**).               |
| `git reflog`       | Shows the history of branch moves (even things not in `git log`—useful for recovery). |

---

# ✅ Bonus tips

* 🛠️ **Be careful with destructive commands** like `git reset --hard`, `git clean`, and force-push (`git push --force`).
* 🌀 Use `git help <command>` anytime for detailed built-in documentation.

---

**Do you want examples for specific workflows or diagrams next? Let me know! 😊**
