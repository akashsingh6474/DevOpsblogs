---
title: "Day 50:CI/CD pipeline on AWS - Part-1 🚀"
seoTitle: "AWS Commit local file to AWS code commit"
datePublished: Mon Oct 30 2023 10:34:24 GMT+0000 (Coordinated Universal Time)
cuid: clocrj9lp000d09l8f7lb0ygl
slug: day-50cicd-pipeline-on-aws-part-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698661863688/68940b88-9741-4fcb-a652-f9bf8784ffe8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698661903717/eb0e08af-0bf0-42c3-b79e-970af0a611d9.png
tags: aws, codecommit, 90daysofdevops, awscloud

---

## What is Code Commit ?

* CodeCommit is a managed source control service by AWS that allows users to store, manage, and version their source code and artifacts securely and at scale. It supports Git, integrates with other AWS services, enables collaboration through branch and merge workflows, and provides audit logs and compliance reports to meet regulatory requirements and track changes. Overall, CodeCommit provides developers with a reliable and efficient way to manage their codebase and set up a CI/CD pipeline for their software development projects.
    

# [Task-01 :](https://github.com/akashsingh6474/90DaysOfDevOps/blob/master/2023/day50/tasks.md#task-01-)

* Set up a code repository on CodeCommit and clone it on your local.
    
* You need to set up GitCredentials in your AWS IAM.
    
* Use those credentials in your local and then clone the repository from CodeCommit
    

There are a few steps to follow to complete tasks.

first, go to the AWS account search Code commit and set up your code repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698655249784/7090f51c-3af4-49dd-b103-01fb9a9a8536.png align="center")

* Now, we need to set up Git Credentials in IAM.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698656514224/5eda1466-cc11-4513-a470-f08fcf677aa2.png align="center")
    
    Go to IAM Create User.
    
* Go to IAM &gt; Users &gt; Scroll down to Security Credentials&gt; **HTTPS Git credentials for AWS CodeCommit** \\&gt; Generate Credentials
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698656599804/823eca57-2967-45ea-a299-acff6e6b2d06.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698656684155/96a303f8-23f5-4e5b-84ef-447b9c836575.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698656705313/f54b95bb-d7de-4a56-84a0-556ef0415ee6.png align="center")
    
    Now clone your repository locally.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698659511409/b34efc20-ee2b-4724-ab80-8f679c820914.png align="center")
    
    Go to the repo directory you created now using the cd command.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698659563328/a00600aa-af1c-4058-a06e-72c60929b97d.png align="center")
    
    # Task-02 :
    
    * Add a new file from local and commit to your local branch
        
    * Push the local changes to Code Commit repository.
        
    
    Create a files using:
    
    ```plaintext
    cat newfile.txt
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698659924791/c7ce7017-df6f-4979-badc-f9802fdeab6c.png align="center")
    
    Add these files to the staging area, using:
    
* ```plaintext
    git status
    git add .
    git status
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698659988577/d1f6b710-9ec2-4388-b22f-47a4c06c6771.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698660025225/333bf02a-14ad-4e09-809a-5d412d42d159.png align="center")

To add these in the local repositories history:

```plaintext
git commit -m "Commiting the files I created now"
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698660104019/fa9e7619-f0a9-45ef-8a30-26a23a265d35.png align="center")

Using the following command, push the changes from your local to the CodeCommit repository.

```plaintext
git push origin master
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698660215425/9e3ef51f-5bbd-4936-a1be-f5e885d8b9d5.png align="center")

Verify that the files are pushed into the CodeCommit repository.

In the CodeCommit Repository &gt; Repositories &gt; Code.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698660337669/e497650d-f495-45a7-aa25-3228e275eb86.png align="center")

And yes! You have pushed your local files to the CodeCommit Repository.

In this blog, I have created a repository in CodeCommit, cloned it to the local, and pushed the files from local to the CodeCommit. If you have any questions or want to share your experiences, please comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [**Akash Singh.**](https://www.linkedin.com/in/akash-singh-70o) Do reach me and I am open to suggestions and corrections.

#Day50 #90daysofdevops