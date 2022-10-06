# GIT Cheat-Sheet

### Glossary

| Keywords                     | Description                                                                                                             |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| git                          | Open-source distributed version-control system, used to store code in repositories                                      |
| GitHub, GitLab and Bitbucket | Platform for hosting and collaborating on Git repositories                                                              |
| staging                      | Proposed files/directories that you'd like to commit                                                                    |
| commit                       | Saving all staged files/directories to your local repository                                                            |
| branch                       | An independent line of development, so you can develop features isolated from each other. Master branch is the default. |
| clone                        | Local version of a repository, including all commits and branches                                                       |
| remote                       | Common repository on eg. Github that all team members to keep that changes in sync with                                 |
| fork                         | Copy of a repository owned by a different user                                                                          |
| pull request                 | A method of submitting contributions to a repository                                                                    |
| HEAD                         | Represents your current working directory                                                                               |

### Configuration

| Key/Command                              | Description                                         |
| ---------------------------------------- | --------------------------------------------------- |
| `git config --global user.name [name]`   | Set author name to be used for all commits          |
| `git config --global user.email [email]` | Set author email to be used for all commits         |
| `git config color.ui true`               | Enables helpful colorization of command line output |

### Core Commands

| Key/Command                 | Description                                              |
| --------------------------- | -------------------------------------------------------- |
| `git init [directory]`      | Creates new local repository                             |
| `git clone [repo]`          | Creates local copy of remote repository                  |
| `git add [directory]`       | Stages specific [directory]                              |
| `git add [file]`            | Stages specific [file]                                   |
| `git add -A`                | Stages all changed files                                 |
| `git add .`                 | Stages new and changed files, NOT deleted files          |
| `git add -u`                | Stages changed and deleted files, NOT new files          |
| `git commit -m "[message]"` | Commit everything that is staged                         |
| `git status`                | Shows status of changes as untracked, modified or staged |

### Synchronization of Changes

| Key/Command   | Description                                                                           |
| ------------- | ------------------------------------------------------------------------------------- |
| `git fetch`   | Downloads all history from the remote branches                                        |
| `git merge`   | Merges remote branch into current local branch                                        |
| `git pull`    | Downloads all history from the remote branch and merges into the current local branch |
| `git push`    | Pushes all the commits from the current local branch to its remote equivalent         |

*Tip: `git pull` is the combination of `git fetch` and `git merge`*

### Undo Changes

| Key/Command                 | Description                                                                                 |
| --------------------------- | ------------------------------------------------------------------------------------------- |
| `git checkout -- [file]`    | Replace file with contents from HEAD                                                        |
| `git revert [commit]`       | Create new commit that undoes changes made in [commit], then apply it to the current branch |
| `git reset [file]`          | Remove [file] from staging area                                                             |
| `git reset --hard HEAD`     | Removes all local changes in working directory                                              |
| `git reset --hard [commit]` | Reset your HEAD pointer to previous commit and discard all changes since then               |

### Branches

| Key/Command                | Description                        |
| -------------------------- | ---------------------------------- |
| `git branch [branch]`      | Create a new branch                |
| `git checkout [branch]`    | Switch to that branch              |
| `git checkout [branch] -b` | Create and checkout new branch     |
| `git merge [branch]`       | Merge [branch] into current branch |
| `git branch -d [branch]`   | Deletes the [branch]               |
| `git push origin [branch]` | Push [branch] to remote            |
| `git branch`               | Lists local branches               |
| `git branch -r`            | Lists remote branches              |
| `git branch -a`            | Lists local and remote branches    |

### History

| Key/Command                | Description                                                      |
| -------------------------- | ---------------------------------------------------------------- |
| `git log`                  | Lists version history for the current branch                     |
| `git log --author=[name]`  | Lists version history for the current branch from certain author |
| `git log --oneline`        | Lists compressed version history for the current branch          |
| `git show [commit]`        | Outputs metadata and content changes of the specified commit     |
| `git blame [file]`         | Shows who changed what and when in file                          |

### Gitignore

You can list files/directories that you want to explicitely exclude from Git in a `.gitignore` file. This file should be placed at the root of your repository.

It is noted that people usually exclude dependency caches, such as `node_modules`, system files, such as `.DS_Store`, among others.

You can see the `.gitignore` file of [this repository](https://github.com/0nn0/git-basics-cheatsheet/blob/master/.gitignore) or [more examples](https://github.com/github/gitignore) provided by GitHub.


### Creating local repositories

To turn a folder into a git repository you need the following git command:

---

```shell
cd path/to/my/folder
git init
```

> ❗️ Do not initialize a git repository inside another git repository!  
> To check if a folder has already been initialized you can run the following git command
>
> ```shell
> git status
> ```
>
> Not a git repo:
>
> ```shell
> fatal: not a git repository (or any of the parent directories): .git
> ```
>
> A git repo:
>
> ```shell
> On branch main
> nothing to commit, working tree clean
> ```
---

## Committing in a local repository

We recommend executing the following git commands for every completed task:

> 💡 Hint: Commits help track your progress.  
> Commit early, commit often.   > Make sure, that your code works as expected.
| Git command                      | Git task                                         |
| -------------------------------- | ------------------------------------------------ |
| `git status`                     | List all files that have changed and their state |
| `git add <filename>`             | Add a file to the stage                          |
| `git commit -m "Commit message"` | Create a commit including all staged files       |
| `git log --oneline`              | Show the commit history                          |


---

## Using commits as backups

You can always return to the last committed state of the entire project:

```sh
git restore .
```

You can also restore individual files:

```sh
git restore <file name>
```

---

## Connecting to a remote repository

This enables teams to work on the same remote repository and clone it locally. The remote repository
also serves as a backup.

### Connecting your local repository to a new remote repository

The first thing you need to do is create a new empty remote repository on GitHub. You will then see
some hints e.g. "...or push an existing repository from the command line". **Copy the commands from
GitHub** and execute them in your local project folder.

**Example:**

```
git remote add origin git@github.com:GitHubUsername/repository-name.git
git branch -M main
git push -u origin main
```

### Cloning a remote repository

You can create a copy of the remote repository on your local machine with the following command:

```shell
git clone <url>
```

> 💡 You can find the url of remote repositories on GitHub on the repository page. Please use the
> SSH url.
<img src="assets/clone-ssh.png" alt="Clone SSH" width="400">

### Synchronizing local & remote repositories

| Git command | Git task                                    |
| ----------- | ------------------------------------------- |
| `git push`  | Upload content to the remote repository     |
| `git pull`  | Download content from the remote repository |

---

## Resources

- [Connect with SSH Docs on GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/about-ssh)
- [Git SCM](https://git-scm.com/)
- [Git book](https://git-scm.com/book/en/v2)
- [Git Cheatsheet](https://training.github.com/downloads/github-git-cheat-sheet/)

Workflow

Repository
Commit
