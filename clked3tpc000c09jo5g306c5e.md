---
title: "Basic Git & GitHub for DevOps Engineers."
datePublished: Sat Jul 22 2023 18:47:12 GMT+0000 (Coordinated Universal Time)
cuid: clked3tpc000c09jo5g306c5e
slug: basic-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690044491531/35e7677f-27ca-4457-9f86-363e26d4d923.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690051614726/49ef4cb3-39ce-4efb-bb1e-4e85de9666ce.png
tags: cloud, github, git, devops, 90daysofdevops

---

### **⚒️Introduction**.

Welcome to Day 8 of the #90DaysOfDevOps challenge! Today, we’ll learn about GIT and GitHub. We often use these words interchangeably, but they both are not the same. In the fast-paced world of software development, collaboration, version control, and continuous integration are vital components of successful DevOps practices. Git and GitHub have emerged as essential tools in the DevOps engineer’s weapons, enabling teams to streamline workflows, improve code quality, and foster efficient collaboration. In this blog, we’ll explore the fundamentals of Git and GitHub, their significance in the DevOps ecosystem, and how they revolutionize the way development teams work together to deliver exceptional software.

### **🔥What is Git?**

Git is a distributed version control system used for tracking changes in source code during software development. It was created by Linus Torvalds in 2005 and has since become one of the most widely used version control systems in the world. Git is open-source, which means its source code is freely available for anyone to use, modify, and distribute. Everyone maintains a local repository of their own which contains all the files & metadata present main repository.

![Git — commands you need to git going! | by Dave O'Dea | Medium](https://miro.medium.com/v2/resize:fit:686/1*diRLm1S5hkVoh5qeArND0Q.png align="left")

### 🎭Drawback of Git.

1. It is not locally available, meaning you always need to be connected to a network to perform any action
    
2. Since everything is centralized if control server gets failed then you will lose your entire data e.g. SVN tool.
    

### 🐈‍⬛What is GitHub?

GitHub is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

### **🛞What is Version Control?**

Version control is a system that tracks changes to a file or set of files over time so that you can recall specific versions later. It allows you to revert files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.

There are two types of control systems

1. CVCS( Centralised control version system)
    
2. DVCS ( Distributed control version system)
    

### **⚙️CVCS( Centralized control version system)**

➡️In the cvcs a client need to get a local copy file of the source from the server, do the changes and commit those changes to the central source on the server.

➡️cvcs system is easy to learn and set up.

➡️Working on branches in different ini cvcs develop or often faces merge conflict.

➡️cvcs system does not provide offline access.

➡️If cvcs server is down developer can't work.

![Version Control Systems - GeeksforGeeks](https://media.geeksforgeeks.org/wp-content/uploads/20190624140224/cvcss.png align="left")

### ⚙️DVCS ( Distributed control version system)

➡️In dvcs each client can have a local branch as well and have a complete history on it client needs to push the changes to the branch which will then be pushed to the server repository.

➡️dvcs systems are difficult for beginners multiple commands need to be recommended

➡️working on branches is easier in dvcs developer faces less conflict

➡️dvcs system is working fine on offline mode as a client copies the entire repository on their local machine

➡️dvcs is faster as mostly user deals with a local copy without hitting the server every time.

➡️If dvcs server is down developers can work using their local copies.

➡️Overall, the decentralized nature of a DVCS allows for greater collaboration, flexibility, and security, making it a popular choice for many teams.

![How does Git work?. Git is a DVCS (Distributed Version… | by sunil kumar  sahoo | Medium](https://miro.medium.com/v2/resize:fit:1400/1*gPBljo_uRh-IBtHY2oB7ig.png align="center")

### **🧑‍💻Install Git on your computer:**

You can download it from the official website at

[git-scm.com/downloads](http://git-scm.com/downloads)

```bash
sudo apt-get install git init
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049441282/cdcb1e6f-aa1a-4904-8ef2-c0ad20de1d23.png align="center")

# **🐈‍⬛Create a free account on GitHub:**

`You can signup from:` [github.com](http://github.com)

**Some Basic Commands of Git.**

```bash
Command          Description

git init         Initializes a new Git repository in the current directory.

git clone        Creates a local copy of a remote repository.

git add          Adds changes or new files to the staging area for the next commit.

git commit       Records changes to the repository with a commit message.

git status       Shows the status of the working directory and staging area.

git push         Uploads local commits to a remote repository.

git pull         Fetches and merges changes from a remote repository.

git branch       Lists, creates, or deletes branches in the repository.

git checkout     Switches to a different branch or restores files from a commit.

git merge        Combines changes from one branch into another branch.

git log          Displays a history of commits in the repository.

git remote       Manages remote repositories linked to the local repository.
```

# **☁️Create a new repository on GitHub and clone it to your local machine**

**step 1:** Sign in to your GitHub account using your username and password.

**step 2:** Once you are signed in, click on the “+” icon in the top-right corner of the GitHub homepage. From the dropdown menu, select “New repository.” or, go to repositories and click on ‘new’ in the top right corner.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049679568/1573d5ed-99d4-4c95-9324-6daaf5d824e0.png align="center")

**Step 3:** Set up the repository: Now Add the repository name and other details like whether you want to keep it public(publically accessible) or private repo.

Then click on ‘create repository

you have successfully created a repository.

**step 4:** After creating the Repository it will look something like this :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049790187/56ef96ca-7f1d-465e-9ba1-474d8e733553.png align="center")

## **☁️Clone Repo to the local machine✨**

**step1:** click on &lt;&gt;code, after that, we can see a path, and copy that path

**step 2:** let's go into your local machine.

**step 3:** git clone &lt;paste\_the\_copied\_link\_here&gt;

it will clone your repository into your local.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690049887887/f84a9096-f273-4656-ab4b-080f5e6788fc.png align="center")

## **📝Make some changes to a file in the repository and commit them to the repository using Git**

Create a few files or do the code you want to and then commit them.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690050254172/7d17c9f1-797b-4d19-823d-6d6ae67a1343.png align="center")

We have created 2 files and added a few line of code in each file.

We will now commit these changes but to commit we will add them to the staging directory and then commit them.

In the below screenshot using `git status` command, you can track your code stage, and track them using `git add` command. This is the following command useful for committing code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690113296995/aaba0e0f-548d-4a55-8238-cecd7ad85749.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690113353230/d513d31d-91c5-47cc-8433-f566bdf2a7be.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690113409544/8444a59f-e424-4f85-8a33-4e0e786c888a.png align="center")

### **🎭Git Log :**

you can use this command to see the commit id and commit massage.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690050728483/26577ceb-7b73-4be6-a791-bdb5db0454b5.png align="center")

## **📌Push the changes back to the repository on GitHub.**

```bash
git push origin <branch-name>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690114491521/b0f94c62-0bdd-4944-abab-7123280e77c6.png align="center")

### **📍Conclusion:**

Above mentioned information is much important for a DevOps engineer as he has You’ve mastered the art of Git and GitHub, joining the ranks of legendary DevOps engineers! Embrace version control and collaboration, and your coding adventures shall know no bounds!

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**