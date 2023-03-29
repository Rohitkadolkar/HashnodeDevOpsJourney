---
title: "#Day10 : Advance Git & GitHub for DevOps Engineers. #90DaysofDevOps"
datePublished: Wed Mar 29 2023 00:50:32 GMT+0000 (Coordinated Universal Time)
cuid: clfsz09f1000109mj56xt6aef
slug: day10-advance-git-github-for-devops-engineers-90daysofdevops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1680050966494/c50cf498-b7e2-4bb4-bcdb-786508fc4a07.webp
tags: linux, github, version-control, git, devops

---

## Git Branching

Use a branch to isolate development work without affecting other branches in the repository. Each repository has one default branch, and can have multiple other branches. You can merge a branch into another branch using a pull request.

Branches allow you to develop features, fix bugs, or safely experiment with new ideas in a contained area of your repository.

## Git Revert and Reset

Two commonly used tools that git users will encounter are those of git reset and git revert . The benefit of both of these commands is that you can use them to remove or edit changes you’ve made in the code in previous commits.

The **git revert** command is **a forward-moving undo operation that offers a safe method of undoing changes**. Instead of deleting or orphaning commits in the commit history, a revert will create a new commit that inverses the changes specified. Git revert is a safer alternative to git reset in regards to losing work.

The **git reset** is the command we use when we want to move the repository back to a previous `commit`, discarding any changes made after that `commit`.

Step 1: Find the previous `commit`:

![Git Reset Step 1](https://www.w3schools.com/git/img_reset_part1.gif align="left")

Step 2: Move the repository back to that step:

## Git Rebase and Merge

### What Is Git Rebase?

Git rebase is a command that lets users integrate changes from one branch to another, and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs.

### What Is Git Merge?

Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.

The merge wording can be confusing because we have two methods of merging branches, and one of those ways is actually called “merge,” even though both procedures do essentially the same thing.

## Task 1:

### Add a text file called version01.txt inside the Devops/Git/ with “This is first feature of our application” written inside. This should be in a branch coming from `master`

`git clone <URL>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680036785818/3deae908-edcc-49c5-b2fd-81ac6d6af263.png align="center")

**Make sure you are present in the main branch, Create branch dev**

`git branch <branch name>`

`git checkout <branch name>`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680036978865/a576c7fa-e121-4cbc-8549-2eb067833add.png align="center")

**Create a file name version01.txt & add content to it "This is the feature of our application"**

`vim version01.txt`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680037206032/8c30dfd4-26a1-432e-9ccf-e48db3bd5d76.png align="center")

**Now add and commit it with message "new feature added"**

**git commit -m "new feature added"**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680037307313/40ab2cce-f36f-4f25-8c93-2de7ccdf387b.png align="center")

## Task 2

### Add new commit in `dev` branch after adding below mentioned content in Devops/Git/version01.txt: While writing the file make sure you write these lines

* **1st line&gt;&gt; This is the bug fix in development branch**
    
* **Commit this with message “ Added feature2 in development branch”**
    
* **2nd line&gt;&gt; This is gadbad code**
    
* **Commit this with message “ Added feature3 in development branch**
    
* **3rd line&gt;&gt; This feature will gadbad everything from now.**
    
* **Commit with message “ Added feature4 in development branch**
    

**For this, just add and commit each time a change is made and and changes can be verfied using:**

`git log`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680037752681/fdb174a4-97e6-43c1-8d25-0352370edb26.png align="center")

## Task 2:

* ### Demonstrate the concept of branches with 2 or more branches with screenshot.
    
* ### add some changes to `dev` branch and merge that branch in `master`
    
* ### as a practice try git rebase too, see what difference you get.
    

**Below you can see two branches out of master branch, which can be created for working on different features on the master branch**

`git branch`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680039830238/64589d76-9ab4-4ad7-bf1d-82c57d1ba786.png align="center")

**As we have already made changes to dev branch, lets merge it to master**

`git checkout master`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680041441301/b1259a24-0eab-4409-b7ef-f5a962239052.png align="center")

**When we open the git master branch we can see that there isnt a version01.txt file as it is created in dev branch.**

**Being in master branch, try to merge dev branch to master:**

**git merge &lt;branch to merge to current branch&gt;**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680042083913/af6ecba1-dec3-4091-8b60-fd90efa580eb.png align="center")

**Do** `ll` **and check:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680042146363/909ce386-7e13-4070-8b9f-692c75893d5e.png align="center")

**The version01.txt can be seen in the master branch.**

### Git Rebase

In Git merge, what we do is take make a branch from the master branch or any branch for that matter to add some features. Later, we add commits to it and then merge the branch back with its parent branch from which it was created. This creates a workflow that looks something like this -

![Git Merge | Atlassian Git Tutorial](https://wac-cdn.atlassian.com/dam/jcr:83323200-3c57-4c29-9b7e-e67e98745427/Branch-1.png?cdnVersion=kq align="left")

This, when done on a major scale or when added too many branches or features would look like a complicated tree of branches.

To overcome this Rebase is a better workflow option. What it does is it adds the commits that were made in the branch ahead of the master branch commits that existed before merging the file. The workflow would look something like this :

![Interactive Rebase in SourceTree - DZone Java](https://www.becomebetterprogrammer.com/wp-content/uploads/2021/12/git-rebase.png align="left")

This makes the structure look less complex and understandable.

**Lets try doing a commit on dev branch and rebase it to master.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1680044272635/4de362e1-5347-45e5-b4ce-222d2b3abfa7.png align="center")

Thank you!