# Version Control in Git

## 1. Introduction
* Version is the contents of a file at a given point in time. It also includes metadata, or information associated with the file, such as the author, where it is located, the file type, and when it was last saved
* Version control is a group of systems and processes to manage changes made to documents, programs, and directories
* Version control isn't just for software. Anything that changes over time or needs to be shared can benefit from using version control
* Version control allows us to track files in different states and let multiple people work on the same files simultaneously, a concept known as continuous development
* It also allows us to combine different versions, identify a particular version of a file, and revert changes
* One popular program for version control is called Git
* Git is open source and scalable to easily track everything from small solo projects to complex collaborative efforts with large teams!
* Note that Git is not the same as GitHub, which is a cloud-based Git repository hosting platform. However, it's common to use Git with GitHub
* A key benefit of Git is that it stores everything, so nothing is ever lost
* Also, Git automatically notifies us when our work conflicts with someone else's, so it's harder to accidentally overwrite content
* Additionally, Git can synchronize work done by different people on different machines.

### Saving Files and Commiting
* A Git repository consists of 2 parts:
   * Files and directories we create/edit
   * A directory called .git, which stores all extra information that Git records about the project's history
* .git is located in the main directory of the repo
* Git expects this information to be laid out in a particular way, so we should not edit or delete .git
* Git workflow:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/94b94632-42ec-4729-87b1-beec260c7ea8)
* To save a modified file:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/f4f2392b-2f72-4e17-a501-b64e11390af0)
* To commit the drafts
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/09fa1305-8baf-4fe5-aa0b-7143d9ce997e)
* If we are making lots of changes then it's useful to know the status of our repo
* We can use the git status command, which tells us which files are in the staging area, and which files have changes that aren't in the staging area yet.
* In this case, we see report.md has been modified and is in the staging area, so we make a commit:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/22ed3b01-bb24-4c2a-b2f9-5bcea77ed288)
* Comparing an unstaged file with the last commit: `git diff filename`
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/e8c76d95-2357-4cf7-a87a-a9e605578dff)
* Comparing a staged file with the last commit: `git diff -r HEAD filename`
* Adding HEAD, which is a shortcut for the most recent commit, allows us to see a difference between the report file in the staging area and the version in the last commit
* To compare multiple staged files with last commit, we omit the filename in the command:
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/83d950be-d378-4333-b35c-c6b343d567d1)

## 2. Making Changes
### Storing data with Git
* Git stores data through commits, which have three parts
* The first is the commit itself, which contains metadata such as the author, commit message, and time of the commit
* The second part is a tree, which tracks the names and locations in the repo when that commit happened.
* For each file listed in the tree, there is a blob (3rd Part), which is short for binary large object. A blob may contain data of any kind. Blobs contain a compressed snapshot of the contents of the file when the commit happened
* To view commit info: `git log`: 
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/f2220c47-9f3c-424d-b27d-69ec09b884ff)
* To find a particular commit which could have brought errors:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/cb002756-e446-4207-bdb5-86ea2989fa2a)
* To see the ouptut of git show:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/2470612e-2394-4dbd-bcc9-4a2da89c903c)

### Viewing changes
* Comparing changes between commits: a staged file with the last commit
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/67668eaf-bf9c-42d6-9b44-3975e2c397cb)
* Using HEAD with git show
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/a9185e0e-4559-429b-aa3f-a6559e240df8)
* Note that `git show` is useful for viewing changes made in a particular commit; while `git diff` compares changes between two commits
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/0e520166-ca5b-4d49-ad3c-202cd2143eb9)
* To show line-by-line changes and associated metadata:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/17e4a167-2ae7-4d21-ab7f-f968c229ea8b)

### Undoing Changes before Committing
* If you accidentally added a file (which you didn't want to save coz you were still working on it), you remove it from the staging area (unstage file):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/18af7a99-fdd2-4cdb-b520-6b4336539be4)
* To undo changes in an unstaged file:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/3b6bc4fe-e92e-45b5-9cd3-dfab716564d8)
* To undo changes to all unstaged files in repo:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/0f1fe37b-63b3-403e-bfd9-b1432b17c963)

### Restoring and Reverting
* To customize log output (especially to confine output to a few commits):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/aea8fbbf-3123-48a7-8824-c222e5a34dae)
* We can also customize git log by date as follows:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/8cedc2d7-da82-4b39-b839-0f8c3213ca35)
* Restoring an old version of a file (Part 1):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/6e705e07-a8c2-4426-bc33-4533c7377ac3)
* Restoring an old version of a file (Part 2):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5477424d-c3f6-4681-a9a2-51bf5c13252c)
* Restoring a repo to a previous state(restore old versions of all files):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/441da7cd-891f-4713-88e8-a28095f8282d)
* Cleaning a repo:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/f9d60384-e747-4c37-9d8b-f9298887f4d9)
  
## 3. Git Workflows
### Configuring Git
* To configure global email:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/6f6220ab-86d8-4824-9b7d-b24046876533)
* To ignore specific files, we put the files in a `.ignore` file:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5e5377c5-9eef-47d9-bacc-2d852200c2f7)

### Branches
* If we are working locally and not using version control, it's common to create subdirectories to store different versions of files
* We'll likely end up with extra files and sub-directories
* Git uses branches to eliminate this problem:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/8a6990c1-c15c-4a8c-a307-56fb5c0bae5b)
* To bring the branches back together, we merge them:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/56924e2b-ae7b-46db-a5d3-023883688868)
* Benefits of branches:
   * Avoid endless subdirectories
   * Allow multiple users to work simultaneously
   * Everything is tracked everything
   * Minimizes the risk of conflicting versions
* To identify branches in our project: `git branch` . The branch prefixed with a * is the branch we are currently in
* To create a new branch:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/2c8f2a9a-3794-46a5-b6bb-d0873dfa93f6)
* To compare branches: `git diff branch1 branch2`

#### Git Merge Branches
* When working on projects, developing across different components is common
* This is a key reason why we should switch between branches, as it allows us to keep making progress concurrently
* For example, imagine we have some code in use to track the performance of our surveys
* We want to test some new ideas, but we don't want to change our existing code until we have confirmed it works. We create a new branch of our repo called testing, and test our new ideas. We can also create a new branch for debugging
* To switch branches: `git checkout branch_name`
* After we finish the task handled in the branch, we merge the branch into main branch (ground truth of the project, hence should always be up to date)
* We can merge branches using: `git merge source destination`
* The output of the merge command is:
  * Last commit hashes from each branch (2)
  * Type of merge e.g. Fast-forward --> meaning additional commits were made on the summary-statistics branch, so Git brings the main branch up to date
  * Number of lines added or deleted per file

### Handling Git Conflicts
* A conflict occurs when a file in different branches has different contents that prevent them from automatically merging into a single version
* Output of opening conflicting file using nano text editor:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/d94fc9b7-86ce-4e3d-9acb-7c7da4a91176)
* To resolve the conflict:
  * Delete all conflicting lines and remain with the relevant line, and save the file
  * Add the modified file to staging area: `git add modified_file`
  * Commit it to main branch: `git commit -m "Resolving file conflict"`
  * Merge updated branch into main again: `git merge updated_branch main`
* So, in the case of conflicts, prevention is definitely better than cure
* While it's important that we know how to deal with conflicts, the best approach is to lower the chances of conflicts occurring
* The ideal approach is to use each branch for a specific task. We should avoid editing the same file in multiple branches.
* While it doesn't guarantee we'll avoid creating a conflict, it does reduce the risk

## 4. Collaborating with Git
### Creating repos
* To create a new repo:
  * Create repo: `git init repo_name`
  * Cd to repo directory: `cd repo_name`
  * Confirm git repo has initialized correctly: `git status`
* To convert an exisiting project into a repo:
  * Convert the directory to a Git repo: `git init`
  * Add files and commit
* We should avoid creating a Git repo inside another Git repo, also known as nested repos --> this creates 2 .git directories
* Unfortunately, as we try to make commits, Git will get confused about which directory it needs to update
* Generally, nested repos are not necessary except when working on extremely large and complex data projects

### Working with remote repos (remotes)
* A remote repo is a repo stored in the cloud through an online repo hosting service such as GitHub
* Key benefits to using remotes
  * If our computer breaks down or we lose it, we can use a different computer to access our project from the remote repo as it is backed up there
  * Colleagues can collaborate with us regardless of their location
* Cloning a local repo:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/3ade0c91-c8c8-4f76-af53-d7f9c0e97a44)
* Cloning a remote:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/a73f21aa-ea15-4228-9004-bad1c97fc684)
* To identify a remote repo: `git remote`
* Specifying name for remote when cloning:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/09457873-b108-4aca-b355-cfbdc2ce4c87)

### Collaborating on Git Projects
#### Gathering from a remote
* If several people are collaborating on a project then, in practice, they will access the remote, work on files locally, save them, and synchronize their changes between the remote and local repos
* This means that the remote repo should be the source of truth for the project, where the latest versions of files that are not drafts can be located
* To compare the files in a remote against the contents of a local repo we first need to fetch versions from the remote:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/7668f2af-38b8-491c-ac02-b3ea5166639e)
* You can also fetch from a different branch by: `git fetch origin branch_ name`
* To synchronize content between the 2 repos:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/c25b6b07-59f1-42c5-a081-c7179fba2d49)
* Git has simplified the process of fetch and merge into one command: git pull
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/056aaeec-14bb-48b4-8e99-28b92a21886f)
* If we have been working locally and not yet committed our changes, then Git won't allow us to pull from a remote. Let's say we've added a new line to the report but not staged the file or made a commit
* If we try to pull from origin then Git tells us that local changes would be overwritten. We are instructed to commit our changes and told that the pull command was aborted
* Therefore, it's important to save our work locally before we pull from a remote

#### Pushing to a remote
* Is the process of bringing our local changes into a remote repo
* Git push syntax:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/dd7a4c50-304d-4319-9bc4-322f2eaeace7)
* Typical git push/pull workflow:
  * We start by pulling the remote into our local repo
  * We then work on our project locally, committing changes as we go
  * Lastly, we push our updated local repo to the remote
  * This workflow is repeated throughout our time working on the project.
* Note that remote/loval conflicts can arise when we don't start the workflow by pulling from the remote
* This can typically occur because while we've been working locally, our colleagues have been pushing their changes to the remote
* So, if we don't pull from the remote at the start of the workflow then our local repo won't be synchronized with the remote
