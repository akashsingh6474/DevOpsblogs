---
title: "Day 10 Advance Git & GitHub for DevOps Engineers."
datePublished: Thu Jul 27 2023 09:37:04 GMT+0000 (Coordinated Universal Time)
cuid: clkkynlkz000d0ame2ahs6vsd
slug: day-10-advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690450551395/142f89df-4b19-4ab3-9a6e-afd3fd3dca56.png
tags: devops, 90daysofdevops, day10

---

### **✅Introduction.**

Hello Everyone welcome back to the new technical blog this is Akash Singh. I hope everyone is doing great and learning new things. today we will learn a deep about git branch, Git merge, git revert, git rebase and git reset will learn how to create a branch how to merge two in a single branch and learn that how to revert a commit how to reset the commit from from the git file. so let's get started ...!!

## ✅What is Git Branch?

In Git, a branch is a lightweight movable pointer to a commit. It is one of the fundamental concepts in Git and is used to work on different features, bug fixes, or experiments in parallel without affecting the main codebase until the changes are ready to be integrated.

**Advantage of the branch.**

Each task has one separate branch

After done with the code, merge other branches with the master.

This concept is useful for parallel development

You can create any no. of branches

Changes are personal to that particular branch

The default branch is "master".

The file created in the workspace will be visible in any of the branch workspaces until you commit once you commit, then that file belongs to that popular branch

When creating new branch data from the existing branch is copied to a new branch.

## ✅Git Revert and Reset

**Git Reset**:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690390380412/29a37ea7-cdc9-4061-903a-2f1508830fed.jpeg align="center")

git reset is a powerful command that is used to undo local changes to the state of a git repo.

To reset the staging area

```bash
git reset <filename>
git reset .
```

To reset the changes from both the staging area and the working directory at a time.

```bash
ggit reset -- hard
```

**Git Revert:**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690390266453/73a2e935-3cd6-46ee-85f1-5f4f738f1573.png align="center")

the revert command helps you undo an existing commit.

It does not delete any data in this process instead rather git creates a new commit with the included files reverted to their previous state so, your version control history moves forward while the state of your files moves backward.

```bash
git revert <commit_id>
```

## ✅Git Rebase and Merge

\*\*Git Rebase:\*\*Git rebase is a command that lets users integrate changes from one branch to another, and the logs are modified once the action is complete. Git rebase was developed to overcome merging’s shortcomings, specifically regarding logs.

![What is Git Rebase?](https://media.licdn.com/dms/image/D5612AQE1Q7CDqNbzwg/article-cover_image-shrink_720_1280/0/1658162333356?e=2147483647&v=beta&t=BGX3yTOvbQSBgZ-5jIrc-LG1VwYFhdBfsmvnDGLdZAA align="left")

**Git merge:** Git merge is a command that allows developers to merge Git branches while the logs of commits on branches remain intact.

The [merge](https://www.simplilearn.com/tutorials/git-tutorial/merge-conflicts-in-git) wording can be confusing because we have two methods of merging branches and one of those ways is actually called “merge,” even though both procedures do essentially the same thing.

![Git Merge | Atlassian Git Tutorial](https://wac-cdn.atlassian.com/dam/jcr:c6db91c1-1343-4d45-8c93-bdba910b9506/02%20Branch-1%20kopiera.png?cdnVersion=1131 align="left")

## **✅The Workings of Git Rebase and Merge.**

Git rebase takes all the changes, and compresses them into a single patch and integrates this new patch onto the target branch. Then, it moves the completed work from one branch to another, typically the master branch. In the process, rebase flattens the history, removing unwanted entries.

Git merge, on the other hand, only changes the target branch and creates a commit, preserving the history of the source branch.

### **Task1.**

a text file called version01.txt inside the Devops/Git/

Now add Content to it,

```bash
cd DevOps/
cd Git/
vi version01.txt
This is first feature of our application
esc :wq
```

Add and commit the file,

```bash
git add . 
git commit -m  "Added new feature"
```

Now, check out to new branch "Dev"

```bash
git branch Dev
git checkout Dev
```

Now, add some more content to it, in version01.txt

```bash
This is the bug fix in development branch
```

Make additional commits to the dev branch by updating the version01.txt file and commit this change with the message "Making the following changes: ...".

```bash
git add Version01.txt
git commit -m "Added feature2 in development branch"
```

## **✅Add a new commit in** `dev` branch after adding the below-mentioned content in Devops/Git/version01.txt: While writing the file make sure you write these lines

* 1st line&gt;&gt; This is the bug fix in the development branch
    
* Commit this with the message “ Added feature2 in development branch”
    
* 2nd line&gt;&gt; This is gadbad code
    
* Commit this with message “ Added feature3 in development branch
    
* 3rd line&gt;&gt; This feature will gadbad everything from now.
    
* Commit with the message “ Added feature4 in the development branch
    

Restore the file to a previous version where the content should be “This is the bug fix in the development branch” \[Hint use git revert or reset according to your knowledge\]

```bash
vi version01.txt
```

Now, we have to get rid of the last two lines, to recover use the below steps,

To Recover to the previous version,

```bash
sudo git log
```

To check the commit id use this command git log with the help you will see every commit id

```bash
git revert a53c29
```

## **✅Demonstrate the concept of branches with 2 or more branches with a screenshot**

```bash
git branch new
```

To create a new branch

```bash
git branch
```

to check all the branches you have created

```bash
git checkout new
```

It is used for switching the branches

## **✅add some changes to** `dev` branch and merge that branch in `master`

In the new branch, we have this content in the "Version01.txt" file,

```bash
git merge <branch_name>
```

this command is used to merge two branches...