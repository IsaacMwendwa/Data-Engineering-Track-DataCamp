# Version Control in Git

## Introduction
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

## Saving Files and Commiting
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
