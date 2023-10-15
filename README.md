### This repository contains useful commands of Git

# Table of Contents

- [Repository](#git-repository)

- [Basics](#basics)

- [Remote Repository](#remote-repository)

- [Branches](#branches)

- [Git Checkout](#git-checkout)

- [Reverting Changes](#reverting-changes)

  - [Git Clean](#git-clean)

  - [Git Revert](#git-revert)

- [Git Subtree](#git-subtree)

# Git Repository

Git initialization:

```sh
git init
```

Delet the Initialized git repository: (This will remove the version control system)

```sh
rm -rf .git
```

Display the status of git repository:

```sh
git status
```

Display commits history:

```sh
git log
```

# Basics

Add all files to staging area:

```sh
git add .
```

Remove all files from staging area:

```sh
git rm --cached -r .
```

Commiting the staging area files:

```sh
git commit -m "Intial Commit"
```

# Remote Repository

Pushing the local git repository to remote git repository:

```sh
git push origin master
```

Pull from remote to local repository:

```sh
git pull
```

Cloning a Remote Repository:

```sh
git clone <url>
```

Merging a Remote Repository:

```sh
git pull origin <branch_name>

```

- This **Merges** the remote repository with local repository.

# Branches

Creating a branch:

```sh
git branch <branch-name>
```

Displaying all the branches:

```sh
git branch
```

Merging the branch with main branch:

```sh
git merge <branch-name>
```

# Git Checkout

Switching Branches

```sh
git checkout <branch-name>
```

Create a new branch and switch to it:

```sh
git checkout -b feature/new-feature

```

Go to the specific commit of the file:

```sh
git checkout <commit-hash>
```

Go to the latest commit of the working branch:

```sh
git checkout <branch-name>
```

This command will update your working directory to the latest commit on the specified branch.

# Reverting Changes

```sh
git reset [options] <commit-hash>
```

This command in Git is a versatile command that allows you to reset the state of your repository to a specific commit.

---

```sh
git reset --soft <commit-hash>
```

The --soft option

- This command will undo the last commit, but keep the changes from that commit in your working directory and staging area.
  - This means that your changes are not lost and are ready to be committed again.

You can then manually unstage or delete the files you want to remove.

```sh
A -- B -- C -- D (HEAD)
```

If you run `git reset --soft B`, you'll get:

```sh
A -- B (HEAD) -- C -- D
```

The commits C and D are effectively "uncommitted," and their changes are in the staging area, ready for a new commit.

---

```sh
git reset --hard <commit-hash>

```

The --hard option

- moves the branch pointer to the specified commit
- resets the staging area (index) to that commit
- discards all changes in your working directory

Use this option with caution, as it permanently deletes your uncommitted changes.

```sh
A -- B -- C -- D (HEAD)
```

If you run `git reset --hard B`, you'll get:

```sh
A -- B (HEAD)
```

Commits C and D are effectively "discarded," and their changes are lost.

---

## Git Clean

If you have new files in your working directory that you want to remove in addition to resetting your branch to the latest commit, you can use the git clean command.

The git clean command is used to remove untracked files and directories from your working directory. Here's how you can do it:

Check for Untracked Files:

```sh
git clean -n

```

Remove Untracked Files:

```sh
git clean -f

```

Be very cautious when using git clean -f because it permanently deletes untracked files and directories, and there's no way to recover them.

## Git Revert

```sh
git revert <commit-hash>
```

This command is used to create a new commit that undoes the changes made by a previous commit.

```sh
A -- B -- C -- D (HEAD)
```

You want to undo the changes introduced by commit C. You can use git revert as follows:

```sh
git revert C

```

After running this command, Git will create a new commit (let's call it E) that undoes the changes from commit C. The commit history will look like this:

```sh
A -- B -- C -- D -- E (HEAD)
```

# Git Subtree

Git subtree is a feature in Git that allows you to embed one Git repository within another as a subdirectory.

This is useful when you want to include another repository's content into your own project, while still keeping them separate, and track changes to the embedded repository as part of your project's history.

```sh
git subtree add --prefix=subdir-name remote-repo.git branch-name
```
