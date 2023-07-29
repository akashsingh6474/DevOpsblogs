---
title: "Day 11 Task: Advance Git & GitHub for DevOps Engineers: Part-2"
datePublished: Sat Jul 29 2023 18:10:16 GMT+0000 (Coordinated Universal Time)
cuid: clkobvagh000709jh5p0r0pjy
slug: day-11-task-advance-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690654136137/2b2add3a-b94b-491b-b2f7-191bf0b9a0aa.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690654197337/6f183f8b-da01-4ee4-8426-6513eac3d4d8.jpeg
tags: aws, github, git, devops, 90daysofdevops

---

### 💡Introduction.

Hello Everyone welcome back to the new technical blog this is Akash Singh. I hope everyone is doing great and learning new things. today we will learn a deep about git& GitHub in this blog I will cover Stash cherry-pick the importance of stash in git and cherry-pick git revert, git rebase and git reset will learn how to create a branch and how to merge two in a so let's get started ...!!

### 🕸️What is Git Stash?

In version control systems, a "stash" is a mechanism that allows you to save your current changes in a temporary storage area without creating a commit. This is particularly useful when you are in the middle of working on something but need to switch to a different task or branch without committing to your unfinished changes.

it's is a very useful command when are working on a branch between if you want to change a branch you can without committing your work you can change your branch and your work will be done smoothly without disturbance.

### 🍒What is Cherry-pick?

Cherry-pick is a command in the Git version control system that allows you to select and apply specific individual commits from one branch to another. It enables you to pick one or more commits and apply them to the current branch, essentially bringing changes from another branch without merging the entire branch.

Imagine you have two branches in your project, and there's a bug fix or a cool feature in one branch that you want to add to another branch without merging the whole branch.

Here's where cherry-pick comes to the rescue!

You can cherry-pick the specific commit from one branch and apply it to another branch. It's like plucking a cherry from one tree and placing it on another tree!

### 🕸️How to resolve merge Conflicts?

Merge conflicts can happen when you try to combine different branches, and Git doesn't know which changes to keep. This can occur when you're merging or rebasing branches that have gone in different directions.

When a conflict occurs, Git will let you know which files have conflicts. You can use the "git status" command to see the list of conflicted files.

Next, you can use the "git diff" command to see the differences between the conflicting versions and understand what needs to be resolved.

### 💪Task-01: staging and some changes

In this task first create a new branch. then add a file then add some content inside the file.

```bash
git checkout -b branch1
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690651572561/3db8c584-a3c9-4da5-8bc1-0f2aa5e07626.png align="center")

Now create the text file "stashfile.txt" with the help of any text editor and add content inside this file

```bash
vi stashfile.txt
this is stashfile
:wq
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690651600083/56bbf92c-ce2b-4175-a93e-bb227c0b677a.png align="center")

In the middle of your work, your team urgently requests you to handle an important task in the main branch. To handle this situation without losing your progress, you can utilize the "**git stash**" command to save your changes without committing them.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690651737645/daf97605-fb10-4192-80ce-87c5317358f2.png align="center")

Now Go to the main branch for work and add a text file inside the file add content and then commit that file.

```bash
git checkout main
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690651825809/8fef0f2d-25d0-434b-bc64-ec525867f5ac.png align="center")

After completing this task you have to go to a diffrent branch for more work.

```bash
git checkout dev
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690652108932/220f4345-442e-415d-9d23-3127e69f5edc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690652176409/4957a393-eee3-482a-bd50-bf8299306b0d.png align="center")

### **💪Task-02 Rebase and Commit**

In this task we will work on the day-10 text file version01.txt in this file we will add some content and change some messages.

First of all open that file with any text editor and add content and commit some message.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690652415462/f0ff9eb7-e04d-4e8d-9f68-0959cc468076.png align="center")

add all the lines given in the task and commit them. after committing all the message

Now create a new branch use of the command "git checkout -b branch name".

and use the "git rebase " **git rebase** to include all the commits from the branch1 branch into the production branch.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690652576146/baa90bfd-20e3-49ae-8451-6be3ac2b77a7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690652864752/8c50bade-b325-4e26-bab6-79f930d39c03.png align="center")

### **💪Task 3: Cherry-picking and Optimizing Features**

In this task, we'll learn about cherry-picking a specific commit from one branch to another and making additional changes to it.

Switch to the production branch and commit the message "Added feature2.2 in development branch".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690653102153/39217e68-84e6-4753-bf24-f3a04cd054c3.png align="center")

Further added some more lines in the version01.txt file

1. This is the advancement of the previous feature
    
2. Added a few more changes to make it more optimized.
    

and Now commit this with this commit message "Optimized the feature"

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690653414043/949520cd-2dd5-44d7-8095-ef3a2cccf018.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690653423406/619a8b4d-0a74-4fe1-96c5-9c4b9b5f8825.png align="center")

### **📌Conclusion:**

Congratulations! You've completed Day 11 of the #90DaysOfDevOps challenge. In this blog post, we covered essential steps in utilizing Git stash rebase conflicts cherry-pick we learned how we can work on different branch while same and save the work without committing that work learnt about the Git rebase and cherry-pick how we can add other content inside the file with the help of cherry-pick we seamlessly connected them to facilitate efficient collaboration. With these insights, you can now confidently manage your projects with Git and GitHub, enhancing your development journey. 🚀💻.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com) **/akashsinghtech40@gmail.com**