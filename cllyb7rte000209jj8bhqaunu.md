---
title: "Day 27 Jenkins Declarative Pipeline with Docker"
datePublished: Wed Aug 30 2023 22:29:23 GMT+0000 (Coordinated Universal Time)
cuid: cllyb7rte000209jj8bhqaunu
slug: day-27-jenkins-declarative-pipeline-with-docker
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693434549066/f2c5bbd4-29a3-455a-a284-a78ff52a69c5.png
tags: aws, devops, jenkins, pipeline, ci-cd

---

### **Introduction**

Creating a comprehensive Jenkins CI/CD project with thorough documentation is a vital step in modern software development. Such a project not only accelerates the delivery of high-quality software but also fosters collaboration and repeatability among development teams. This guide will delve into the process of setting up an end-to-end CI/CD pipeline using Jenkins for a Node.js web application. The documentation will provide an insightful roadmap for newcomers and serve as a handy reference for experienced developers.

I created a simple declarative pipeline for Hello World. Now Today we will create a pipeline for the Django application.

# Task:

* Create a docker-integrated Jenkins declarative pipeline
    
* Use the above-given syntax using `sh` inside the stage block
    
* You will face errors in case of running a job twice, as the docker container will be already created, so for that do task 2
    

Follow a few steps to create a declarative pipeline.

1. login into the Jenkins dashboard and click on **CREATE A JOB**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693429254837/6808ab3f-f482-489d-bc50-3a4c7e1e0a6d.png align="center")

1. Enter the job/item name and select **PIPELINE PROJECT.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693429373638/af2ead33-feb6-4cc5-b245-0c11376e28fe.png align="left")

1. Give the description of this job and copy and paste the **GitHub Repo URL under the GitHub Project Section.**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693430528808/e674c25d-26c6-40bc-95e7-837032b8e250.png align="center")
    
2. Choose the option GitHUb Hook trigger, So that webhook will apply the changes made to the GitHub repo automatically.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693430572661/0ba1f178-a989-4ca6-9cd8-3f349ef9fe5d.png align="center")
    
3. Go to **GitHub repo Settings &gt;&gt; Webhooks &gt;&gt; Add Webhook**, Now add the webhook in the below-given format: **http://&lt;jenkins\_public\_ip:8080&gt;/GitHub-webhook/**
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693430625742/a97da700-d00c-4643-a908-622b931df9a6.png align="center")
    
4. Now Set the Credentials, Go to Dashboard &gt;&gt; manage Jenkins&gt;&gt; credentials &gt;&gt; add Credentials.
    

Here select the type of credential, and enter the username, password, and description.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693431261624/3620497f-1b20-4725-8d43-60ee2c71111d.png align="center")

1. Under the pipeline section, enter the pipeline script as shown below.
    
    This script includes various **stages - code cloning, build, pushing the built image to the docker hub repo, and deployment.**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693432186458/855364dd-766c-4eb0-9a86-20b168d7c923.png align="center")

The above code will clone the code, build the image, and push the image to the docker-hub repo.

Now build the job / Any small changes made to the GitHub repo will build the job automatically.

To view the webpage, take the jenkine\_public\_ip:8080. Below given is the webpage of the deployed my-django-app.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading! Your support means the world to me. Let's keep learning, growing, and making a positive impact in the tech world together.

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)