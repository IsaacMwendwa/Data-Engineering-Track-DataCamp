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
* To view commit info: `git log`
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

