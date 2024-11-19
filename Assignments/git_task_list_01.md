# Part 1: Introduction to Version Control and Git

### Task 1: Install and Configure Git

#### 1. Configure Git with your username and email

```BASH
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```


`git config --global user.name` sets username globally. When you commits changes in 
repository , it is used is as author for commit.  

`git config --global user.email` sets user email globally. When you commits changes in 
repository , it is used is as email for commit.  


#### 2. View your Git configuration

```BASH
git config --list
```
This command displays list of all configuration settings currently applied by user.
It includes global,local, and system-wide settings.


### Task 2: Initialize a Repository

#### 1. Create a new project folder and navigate to it

```BASH
mkdir MyProject
cd MyProject
```

`mkdir <folder name>` comand Creates new folder in current directory.

`cd <folder name>` changes current directory to folder directory.

#### 2. Initialize it as a Git repository

```BASH
git init
```

`git init` command Initialize `.git` folder in directory, which indicates it is under git version Control 


### Task 3: Create a File and Make Multiple Commits

#### 1. Create a new file and add content:

```BASH
echo "My First Project" > README.md
```

`echo` command creates file with content given between ". . . ." 

 ` >` single arrow indicates that given message will overwrite existing content

 `>>` Double arrow will append the given message to the existing content.


#### 2. Stage the file:

```BASH
git add README.md
```
  Adds file to Stageing Area which to be included in next commit

• Prepares or stages changes (modified, new, or deleted files) to be included in the next commit.

#### 3. Commit the file:

```BASH
git commit -m "Initial commit: Added README.md
```

• Saves or record the staged changes as repository history

• Each commit represents a snapshot of the repository at a specific point in time

#### 4. Make changes to the file:

```BASH
echo "Added a description" >> README.md
```

Appends the content in file with provided "message"  

#### 5.Stage and commit the changes:

```BASH
git add README.md
git commit -m "Updated README with a description"
```

Staged the file for next commit
Saved the staged file as repository history

### Task 4: Check Status and Log

#### 1. Check the repository's current status:

```BASH
git status
```
`git status` dislpays (staged,untracked,modified) files 

• It helps you understand what has changed, what is staged for commit, and what remains unstaged or untracked.


#### 2. View commit history in detail:

```BASH
git log --oneline --graph --decorate
```

`git log` displays commit history of current repository

`--oneline`  Displays each commit in a single line   
`--graph` Visualizes the branch and merge history as a graph.     
`--decorate` Adds labels to indicate branch names, tags, and HEAD pointer.


### Task 5: Create and Clone a Repository

1. Create a repository on GitHub named example-repo.
2. Clone it locally:
```BASH
git clone http://codinggita.com/example-repo
```
`git clone` copies repository from Github to your local


### Task 6: Understanding the Git Workflow

• Example Workflow:
1. Make changes to a file in the working directory  
`echo "Workflow example" > workflow.md`

2. Stage the file:  
`git add workflow.md`

3. Commit the file to the repository:    
`git commit -m "Added workflow example"`.
                                                                    

# Part 2: Working with Repositories

### Task 7: Branching and Merging

1. Create a new branch for a feature:

```BASH
git branch feature-login
git checkout feature-login
```

`git branch <new branch name>`  creates new branch , but remains on current branch you are working on

`git checkout <branch-name>` You want to switch to an existing branch.	

`git checkout -b feature-login` Creates new branch and immediately stary working on it

2. Add a new file and commit changes:
```BASH
echo "Login Page" > login.html
git add login.html
git commit -m "Added login page"
```

3. Merge the feature branch into main:

```BASH
git checkout main
git merge feature-login
```
`git merge` merges current branch to another branch

• Integrates the changes from the feature-login branch into the main branch.

• If there are conflicts, Git pauses the merge and marks the conflicting files for you to resolve it manually.

### Task 8: Handling Merge Conflicts

1. Create two branches:
```BASH
git branch branch-A
git branch branch-B
```
2. Modify the same line in README.md in both branches.

3. Merge branch-A into main:
```BASH
git checkout main
git merge branch-A
```
4. Attempt to merge branch-B into main (this will cause a conflict):

```BASH
git merge branch-B
```
5. Resolve the conflict manually in README.md, then:

```BASH
git add README.md
git commit -m "Resolved merge conflict between branch-A and branch-B"
```

### Task 9: Renaming and Deleting Branches

1. Rename a branch:
```BASH
git branch -m old-branch-name new-branch-name
```

`git branch` command for managing branches

`-m` : The option to rename a branch.

`git branch -m old-branch-name new-branch-name` renames oldBranch > NewBranch

• If you want to change name of branch you are currently working on , then old Brnch name can be ommited

`git branch -m <new branch name>` for renaming current branch

note : `-M` is used to force rename branch 

2. Delete a branch:
```BASH
git branch -d feature-login
```

`-d` : This option is used to delete branch


# Part 3: Advanced Git Operations

### Task 10: Using Git Stash

1. Make changes to a file but don’t commit:

```BASH
echo "Temporary work" >> temp.md
```

2. Stash the changes:

```
git stash
```

Git Stash allows you to temporarily save uncommited changes without commiting them to the repository.

It is used when you want to switch to another branch and perform actions without losing your current work

3. View stashed changes:

```
git stash list
```

`git stash list` shows list of all shashes in your repository

4. Apply the stashed changes:
```
git stash apply
```

`git stash apply` retrives the changes back from most recent stash and apply to to your working directory

5. Drop the stash after applying:

```BASH
git stash drop
```

Deletes the most recent stash from the stash stack.


### Task 11: Rewriting History with Interactive Rebase

1. Create multiple commits:
```BASH
echo "Commit 1" > file1.txt && git add file1.txt && git commit -m "Commit 1"
echo "Commit 2" > file2.txt && git add file2.txt && git commit -m "Commit 2"
echo "Commit 3" > file3.txt && git add file3.txt && git commit -m "Commit 3"
```

2. Squash commits into one:
```BASH
git rebase -i HEAD~3
```

• Rebase allows you to rewrite the commit history of your branch.     
• You can edit, reorder, squash, or delete commits as needed.       
• This is useful for cleaning up commit history before sharing code.


> `-i` : Opens the rebase in interactive mode, allowing you to modify the commit history.

> `HEAD~3`: Specifies the last 3 commits from the current branch (HEAD).


### Task 12: Cherry-Picking Commits

1. Create a new branch:

```BASH
git checkout -b cherry-pick-example
```
 Creates new branch and immediately changes to it

 2. Cherry-pick a specific commit from another branch:

```BASH
git cherry-pick <commit-hash>
```

`git cherry-pick` copies commit from given `<commit-hash>` and and Git applies these changes to your current branch as a new commit.

### Task 13: Tagging Commits

1. Tag the current commit:

```BASH
git tag -a v1.0 -m "Version 1.0 release"
```
Git tags are used to mark specific points in a repository's history as important

Command Breakdown

`git tag` : The command to create a tag         
`-a` : Creates Annotated tag, which includes metadata like author,date,message   
`-m "Version 1.0 release"` :  The message associated with the tag, describing its purpose

2. Push the tag to the remote repository:

```
git push origin v1.0
```
The v1.0 tag is pushed to the remote repository


### Task 14: Working with Remote Repositories

1. Add a remote repository:
```BASH
git remote add origin <repository-url>
```
Adds remote repository to your local

2. Push your changes to the remote repository:

```BASH
git push origin main
```

### Task 15: Forking and Contributing

1. Fork a repository on GitHub.

2. Clone the fork locally:

```BASH
git clone <forked-repo-url>
```

3. Create a new branch, make changes, and push:


```BASH
git checkout -b fix-typo
echo "Typo fixed" >> README.md
git add README.md
git commit -m "Fixed a typo"
git push origin fix-typo
```

4. Open a pull request on GitHub.


# Part 4: Additional Practice

### Task 17: Git Ignore

1. Create a .gitignore file:

```BASH
echo "node_modules/" > .gitignore
```

The .gitignore file is used in Git to specify intentionally untracked files or directories that Git should ignore.











