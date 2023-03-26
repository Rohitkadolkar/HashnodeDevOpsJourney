---
title: "Day 8 Task: Basic Git & GitHub for DevOps Engineers."
datePublished: Sun Mar 26 2023 19:22:50 GMT+0000 (Coordinated Universal Time)
cuid: clfpsf4e7000109js5kejc92x
slug: day-8-task-basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/wX2L8L-fGeA/upload/30e730b41f8648c74051e95f0afff821.jpeg
tags: linux, github, git, devops, 90daysofdevops

---

# What is Git?

Git is a version control system that allows you to track changes to files and coordinate work on those files among multiple people. It is commonly used for software development, but it can be used to track changes to any set of files.

With Git, you can keep a record of who made changes to what part of a file, and you can revert back to earlier versions of the file if needed. Git also makes it easy to collaborate with others, as you can share changes and merge the changes made by different people into a single version of a file.

## What is Github?

GitHub is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

## What is Version Control? How many types of version controls we have?

Version control is a system that tracks changes to a file or set of files over time so that you can recall specific versions later. It allows you to revert files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1. A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check in" the updated files. Examples of CVCS include Subversion and Perforce.
    
2. A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.
    

## Why we use distributed version control over centralized version control?

1. Better collaboration: In a DVCS, every developer has a full copy of the repository, including the entire history of all changes. This makes it easier for developers to work together, as they don't have to constantly communicate with a central server to commit their changes or to see the changes made by others.
    
2. Improved speed: Because developers have a local copy of the repository, they can commit their changes and perform other version control actions faster, as they don't have to communicate with a central server.
    
3. Greater flexibility: With a DVCS, developers can work offline and commit their changes later when they do have an internet connection. They can also choose to share their changes with only a subset of the team, rather than pushing all of their changes to a central server.
    
4. Enhanced security: In a DVCS, the repository history is stored on multiple servers and computers, which makes it more resistant to data loss. If the central server in a CVCS goes down or the repository becomes corrupted, it can be difficult to recover the lost data.
    

Overall, the decentralized nature of a DVCS allows for greater collaboration, flexibility, and security, making it a popular choice for many teams.

## Hands-on:

### Create a new repository on GitHub and clone it to your local machine

**Step1 - Create a directory and initialize it:**

`git init`

`git init <name of directory> - if not in working directory`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679853364768/54f48d21-d812-46b0-9469-7c689e59d7c0.png align="center")

**Step 2 - Create a file and add it to local repo:**

`touch rohit1`

`git add . rohit1`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679853557805/3425372e-d5ed-4bd5-8492-b05a81668764.png align="center")

**Step 3 - The file is now ready to commit, we came status using:**

`git status`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679853650388/f48520bb-5a9b-4e10-864c-b1908f0ea897.png align="center")

**Step 4 - We can see that the file is ready to commit.**

`git commit -m "our message(note to add)"`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679853795758/f427fb9b-6649-4457-831e-ce78ef34a1c4.png align="center")

**If we check git-status now, it will be blank as there is no file remaining to commit**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679853988709/4cffd0e3-77fa-4a42-b70a-aa5a2d057cdb.png align="center")

**Step 5 - Add Central repository here so that we can push our file in central repo:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679854497942/d05098a9-fca4-492e-9c45-269a85390e4b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679854331724/8945be7a-92ae-41bd-8c0c-bd896697e9b9.png align="center")

**Copy the link of your central repository on the Github account**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679854354029/b4b993a5-d1ab-4749-9761-248c78c1dbd4.png align="center")

**Execute command**

`git remote add origin <https link>`

**Step 6 - Try to push on central repository**

`git push -u origin master`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679854978306/43fdc9e6-963b-4bbf-ac58-930194af6294.png align="center")

**It will ask for a username password:**

**In account, go to settings&gt;Developer settings in left pane&gt;Personal access token&gt;tokens(classic)**

**Generate classic token(give all accesses or access will be denied)**

**You can now also see it in your Github account:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679857831739/c6a53db8-be15-4872-a31a-d043d2fbff92.png align="center")

**To pull it from master:**

`git pull origin master`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1679858483164/9095bfdf-2de7-420c-822f-efb4375c5dcb.png align="center")

## **Creating Branch :**

In Git, a branch is a lightweight movable pointer to a commit. Branches are used to create a separate line of development, allowing changes to be made to a codebase without affecting the main codebase until the changes have been tested and merged.

Creating a new branch in Git is a quick and easy process. When you create a new branch, you essentially create a new pointer to the current commit that you are working on. You can then make changes to the codebase, and all of those changes will be made on the new branch.

Thats it for today! See you in the next blog !