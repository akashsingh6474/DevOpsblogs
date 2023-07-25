---
title: "Day9.Deep Dive in Git & GitHub for DevOps Engineers."
datePublished: Tue Jul 25 2023 11:17:04 GMT+0000 (Coordinated Universal Time)
cuid: clki7chqc000h09l57ndjeujg
slug: day9deep-dive-in-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690283814325/c8875c7c-17c3-419c-8b00-da2b9bdf41c6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690283798694/d9bae495-dad8-4d2f-abe4-d5b27338fdd7.jpeg
tags: cloud, github, git, devops, 90daysofdevops

---

### **🧠Introduction.**

Hello Everyone welcome back to the new technical blog this is Akash Singh. I hope everyone is doing great and learning new things. today we will learn a little deep about git & GitHub in the industry git and git hub play very important roles in the workflow they will help you store your information, and projects with the help of creating a repo that will be public and private it depending on and many for things you can do on the git&GitHub so let's get started ...!!

### **🐙What is Git and why is it important?**

Git is a distributed version control system used for tracking changes in source code during software development. It was created by Linus Torvalds in 2005 and has since become one of the most widely used version control systems in the world. Git is open-source, which means its source code is freely available for anyone to use, modify, and distribute. Everyone maintains a local repository of their own which contains all the files & metadata present main repository.

Here are some key reasons why Git is important:

### **📌Version Control.**

It is distributed control system and everyone has a local copy or clone of the file main repository i.e. everyone maintains a local repository of their own which contains all the files & metadata present in the main repository.

**📌Collaboration and Teamwork:**

Git enables collaboration and teamwork with the developer e.g. with the help of many developers can work on a single project and many projects easily

it is easy to learn and it's easy to use

**📌Branching and Merging:**

Git allows developers to create separate brach and features on projects and after fixing them merge all the branches in a single branch. E.g. two people working on a project one is working on creating the header part of a website and the second one is working on the footer part after completing both of the work they will merge both of the branches in a single branch easily and the whole work will be complete with any kind of disturbance with the help of branches. This is very useful for parallel development. you can create no of branches default branch is master.

**🧑‍💻Code Review and Quality Control:**

Git makes it easy to conduct code reviews, where team members can review each other's changes before merging them into the main branch. Code reviews help maintain code quality, catch errors, and ensure that best practices are followed.

### **🐙difference between Git and GitHub?🐈‍⬛**

**🐙Git** is a distributed version control system used for tracking changes in source code during software development. It was created by Linus Torvalds in 2005 and has since become one of the most widely used version control systems in the world. Git is open-source, which means its source code is freely available for anyone to use, modify, and distribute. Everyone maintains a local repository of their own which contains all the files & metadata present main repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690132727901/ec768282-5fa5-47e1-becd-0cfb09aafd18.jpeg align="center")

**🐈‍⬛GitHub** is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690132699461/e00f4aee-9fdb-446c-b8f9-a703eac26c1e.png align="center")

### 🛅difference between local & remote repositories🌐.

**🛅Local Repository:** A local repository is a copy of the version control repository that resides on your local computer. When you clone or initialize a repository on your computer, you create a local copy that contains the entire version history of the project. The local repository allows you to work on the code, make changes, create new branches, and commit your changes without needing a constant internet connection.

**🌐Remote Repository:** A remote repository is a version control repository that exists on a remote server or hosting service (e.g., GitHub, GitLab, Bitbucket). It acts as a centralized location where all developers working on a project can push their changes and pull changes made by others. Remote repositories facilitate collaboration, version tracking, and backup of the codebase.

It helps to work on multiple developers can work on the same project. it's helps you to collaborate with other developers with the help of remote repo you can connect with anyone globally you can contribute on open source platforms.

### **Task1**:

**Set your user name and email address, which will be associated with your commits.**

First, install git in your instance

```bash
sudo apt-get install git init
```

then you can check that git is installed or not with the help of this command

```bash
git  --version
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214701732/4d50f8e7-8c75-410c-b6ff-9cb41f59dba6.png align="center")

\-&gt; Now create a username and email address

```bash
git config --global user.name "Enteryourname"
git config --global user.email "Enteryouremail"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214465367/d85ea2c0-63a2-4003-a25a-88b912931c88.png align="center")

\-&gt;To check username and password use this command

```bash
git config --list
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690214502846/6d1ae92c-0e8c-4611-9b8c-d134daf851e6.png align="center")

### **Task2**:

**Create a repository named "Devops" on GitHub.**

now go into your git hub account

Go to the dashboard and click on the "New" button to create the repository.

it will look like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690215074762/56adc92b-b5e1-4308-a6f6-08b89417ba1b.png align="center")

**Connect your local repository to the repository on GitHub.**

first of all, go into the GitHub dashboard then open your repo.

then click on code this is will in the right-side corner it will look like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690216021909/e60b9b76-1b49-401a-a230-6ebfe32c18cb.png align="center")

Then copy your ssh- key, then open your terminal and type this command to connect your local repository to the GitHub repository

```bash
sudo git clone <ssh-key-url>
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690216304327/5e064943-4c86-441a-9e93-1f546a0fcdf6.png align="center")

**Create a new file in Devops/Git/Day-02.txt & add some content to it**

Now go to the DevOps folder/directory

```bash
cd DevOps/
```

Now create another folder/directory and create a text file and some content inside the file.

```bash
mkdir Git
```

```bash
cd Git/
vi Day-02.txt
welcome to DevOps
esc
:wq
```

to check the file status use the command "git status" With the help of this command you can file is committed or not

```bash
git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281083648/9cf357fb-61c0-4257-9d81-3a82457aba4d.png align="center")

```bash
git add .
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281138079/cb5b8980-53e5-463c-b472-0b68827dc5b5.png align="center")

```bash
git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281177559/e4105001-09e2-4f63-a000-84165e061f64.png align="center")

After the check status of the file the commit your file this commit will show on your GitHub account there will show also the user name who commit to that

```bash
git commit -m "this is first commit"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281203798/154309ee-6696-4766-9fe8-ccba19de4726.png align="center")

```bash
git status
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281229709/c65cf901-3f35-4e5d-a3d2-a30021c00112.png align="center")

you can check the file comment with the help of "git log " where you will see your commit id 40alphanumeric type git log and paste your commit your will comment

```bash
git log
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281245376/4dac0ff9-1148-4544-b035-b531acd426a2.png align="center")

now push your code file on your remote account use of this command ''git push origin main"

```bash
git push origin main
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281263333/cd5f5177-b600-485e-bdc3-1fb18cea6380.png align="center")

To check that your file is now present on your "GitHub account go to the account

and click on your repo. you will your repo name like "DevOps" Click on the you will another folder "Git".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281290735/5cef1922-a0c3-40df-8fda-89cfea7b2f0e.png align="center")

After clicking on "Git" you will see a file name like "Day-02.txt" Click on that now there will show you the file and the file comment on the top.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690281311081/9b024408-c7d3-402b-8733-a002b4a6ae3b.png align="center")

## **📌Conclusion.**

Congratulations! You've completed Day 9 of the #90DaysOfDevOps challenge. In this blog post, we covered essential steps in utilizing Git and GitHub for version control. After creating a repository on GitHub and connecting it to the local repository, we successfully added a new file and pushed changes to GitHub. We delved into the significance of Git as a version control system and explained the difference between the main and master branches. Additionally, we clarified the dissimilarity between Git and GitHub, emphasizing their respective roles. Understanding the difference between local and remote repositories, we seamlessly connected them to facilitate efficient collaboration. With these insights, you can now confidently manage your projects with Git and GitHub, enhancing your development journey. 🚀💻.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: **akashsingh6474@gmail.com**