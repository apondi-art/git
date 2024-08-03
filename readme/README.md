# Git

This project is designed to introduce you to the world of version control and collaboration using Git. Git is a powerful and widely used tool for tracking changes in your projects, collaborating with others, and ensuring the integrity of your code. By exploring Git, you will be able to:

## Features
- Record modifications to files, so you can see what has changed and when.

- Enable multiple developers to work on the same project 
simultaneously without overwriting each other's work.

- Manage different versions of a project to roll back to previous states or experiment with new features.

- Create branches to work on new features or fixes in isolation before merging them back into the main codebase.

## Setting Up Git

- install Git on your machine by following the instructions for your operating system on the official Git website[Git Website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

- Configure Git with your username and email address.
 ## Git commits

- Commit: A commit in Git is a snapshot of your work at a specific point in time. It saves changes and keeps a history of those changes.
- Git Commits: Git commits refer to the collection of all commits in the history of the repository. Each commit represents a new version of your project.
## Steps to initialize git "hello" directory

## Setting Up Directories

Follow these commands to create and navigate through the necessary directories:
1
```bash
mkdir work           
## Create the 'work' directory
```
2
```bash
cd work             
##Navigate into the 'work' directory
```
3
```bash
mkdir hello          
## Create the 'hello' directory inside 'work'
````
4
```bash
cd hello             
##Navigate into the 'hello' directory

```
## Initialize Git Repository:
inside hello directory
```bash
git init

```
## git status 
it displays the current state of the git repository which can be untracked files, files that have been stagedand ready for committ ,branch that you are currently in.
### 1. Initialize the Git Repository

Navigate to the `hello` directory and initialize the Git repository:

```bash
cd path/work/hello
git init
```
### 2.Check the Status
```bash
git status

```
### make two commit changes at the same time
## Using `git add -p` to Stage Changes

When you have changes in your file and you want to make selective commits, you can use `git add -p` to interactively stage portions of those changes. Here’s how to do it:

### Steps to Stage and Commit Changes

1. **Run `git add -p`**

   In your terminal, execute:
   ```bash
   git add -p hello.sh
   
   ```
#### Review the Diff

Git will show you a diff of the changes and prompt:
diff --git a/hello.sh b/hello.sh
index 6a0d9d4..2a0f4a6 100644
--- a/hello.sh
+++ b/hello.sh
@@ -1,5 +1,6 @@
 #!/bin/bash
+# Default is "World"
 name=${1:-"World"}
 echo "Hello, $name"
Stage this hunk [y,n,q,a,d,/,s,e,?]?

### Select e to Edit the Hunk
Press "e" to edit the hunk. This will open the hunk in your default text editor (e.g., nano).
Edit the Hunk

In the editor, you can manually adjust the changes. For example, to only stage the comment, you might see:
```
diff

@@ -1,5 +1,6 @@
 #!/bin/bash
-# Default is "World"
 name=${1:-"World"}
 echo "Hello, $name"
 ```

You can delete or modify lines as needed.

Save and Exit

    In nano: Press Ctrl+X, then Y to confirm, and Enter to save.

Git Stages the Edited Hunk

Git will stage only the changes you kept in the hunk.

Commit the Staged Changes

Finally, commit the changes:
```
bash

git commit -m "Add comment explaining default value in hello.sh"
```
## History
to show the history of working directory, we use git log command. The command includes commit done on the repository which directly or indirectly reflects the changes made on the files over the time
#### Showing the history of working directory
```
git log inside hello folder  in the work folder
```
```
bash 
git log
```
- To show a one-line history with only commit hashes and messages, you can use the "--oneline" option with the git log command. This will display each commit on a single line with its abbreviated commit hash and commit message.
```
bash
git log --oneline
```
### Controlled Entries
You can customize the git log output using various options to control the number of entries displayed or to filter commits by time range. Here’s how you can do both:
 - for example you can display the last  2 entries,commits made within the last five minutes or you can also combine them all.
 #### last two entries
 To display the last two entries in Git's commit history, you can use the git log command with the "-n" option to specify the number of commits you want to see."--oneline" , Shows each commit on a single line with its abbreviated commit hash and commit message. Here's how you can do it:
 ```
 bash

 git log -n 2 --oneline

```
#### Commits made within the last 5 minutes
To view commits made within the last 5 minutes, you can use the git log command with the "--since "option. Here’s the command to filter commits made in the last 5 minutes:
```
bash
git log --since="5minutes ago" --oneline
```
## Personalized Format:
It is customized way on how information is being displayed.
Personalized format, including the commit hash, date, message, branch information, and author name

```
bash
git log --pretty=format:"%h %ad | %s (%d) [%an]" --date=short
```
### Check it out
#### Restoring the first Snapshot
Restoring the first snapshot (or first commit) in Git typically means reverting your working directory to the state it was in at the very first commit of your repository. This is a way to view or return to the state of the project at that initial point in its history.
it includes following steps:
##### Find the First Commit Hash:
Use the below command to get the hash of the first commit
```
bash
git rev-list --max-parents=0 HEAD
```
##### Check Out the First Commit
Switch to the state of the first commit using the hash you found:
For example:
```
bash
git checkout 23a3c479

```
##### Print the Content of hello.sh

With the working directory now set to the state of the first commit, you can view the content of hello.sh:
```bash
cat hello.sh
```
##### Return to Your Previous Branch

After viewing the file, return to your previous branch (e.g., main or whatever branch you were working on):
```
bash
git switch -
```
#### Restore Second Recent Snapshot: 
##### Find the Second Most Recent Commit Hash

You need to identify the hash of the second most recent commit. You can use git log to view the commit history:
```
bash
git log --oneline
```
##### Check Out the Second Most Recent Commit

To switch to the state of this commit, use:
```
bash
git checkout <second-commit-hash> e.g aadd104
```
##### View or Work with the Restored State

You can now view or work with your files as they were in that commit. For instance, to print the content of hello.sh, use:
```
bash 
cat hello.sh
```
##### Return to Your Branch

After examining or working with the state of the second most recent commit, switch back to your original branch (e.g., main):
```
bash
git switch -
```
#### Return to Latest Version: 
To return to original branch and ensure that it has the latest version :
```bash
git checkout main
```
Then :
```
bash 
cat hello.sh
```
## TAG me
Tags are often used to mark release points (e.g., v1.0, v2.0) or significant milestones in the project.
### Referencing Current Version: 
Referencing the current version of your Git repository can involve identifying the latest commit or tag that signifies the current version. Here’s how you can manage and reference the current version:
#### Steps involves
- git checkout to the branch where you were to add tag
```bash
bash 
git log
```
Or just revert directly to the current version by:
```bash
bash
git rev-parse HEAD
```
```bash
git checkout <hash>
```

- inside the branch , check whether it has a recent tag
```bash
bash
git describe --tags
```
- If not , then add tag
```bash
bash
git tag -a <tag name> -m "message"
```
## Tagging Previous Version:
Git provides a way to refer to commits relative to the current commit without needing to use specific hashes. The notation HEAD~1 refers to the commit right before the current commit.
```bash
bash
git tag -a v1-beta HEAD~1 -m "Tagging the previous version as v1-beta"
```
## Navigating Tagged Versions: 
Navigating tagged versions in Git is a common task, especially when you want to inspect, work with, or check out specific versions of your project that have been tagged. Here’s how you can navigate through tagged versions:
### Move back and forth between the two tagged versions, v1 and v1-beta.
To move back and forth between two tagged versions, such as v1 and v1-beta, you can use the git checkout command. Here’s how you can do it:
```bash
bash

git checkout v1
```
This command puts your working directory in a "detached HEAD" state at the v1 tag, meaning you’re not on a branch but at the exact commit where v1 points.
Checkout the Second Tag (v1-beta)

While still at v1, you can "git checkout v1-beta"
Then you finally git checkout maste to return to the origanal version




















