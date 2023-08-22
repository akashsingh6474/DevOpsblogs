---
title: "Day 23 :Jenkins Freestyle Project for DevOps Engineers."
datePublished: Tue Aug 22 2023 20:51:19 GMT+0000 (Coordinated Universal Time)
cuid: cllms6u83000c0aju0ktngwuz
slug: day-23-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692737345566/bfe002fa-2691-4f33-b3ce-95eee347076b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692737421083/c1c3925b-99ae-49eb-94af-0f77365f5e20.png
tags: aws, devops, 2articles1week, jenkins-devops, 90daysofdevops

---

## What is CI/CD?

### **Continues Intregration:**

CI or Continuous Integration is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration. The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality and reduce the time it takes to release new feature updates.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692029141039/e3265944-e9a8-4387-a036-e5eca3838fa7.png?auto=compress,format&format=webp&auto=compress,format&format=webp align="center")

### **Continuous Deployment:**

Continuous Deployment aims at continuously releasing the code changes into the production environment.

![Continuous deployment | Atlassian](https://wac-cdn.atlassian.com/dam/jcr:1ebe6373-ebd0-46f4-9b76-791ea2be9d56/cd-diagram@2x.png?cdnVersion=1156 align="center")

### **Continuous Delivery:**

CD or Continuous Delivery is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time.

![Understanding Continuous Delivery | TeamCity CI/CD Guide | JetBrains](https://www.jetbrains.com/teamcity/ci-cd-guide/img/Understanding_Continuous-Delivery.svg align="center")

## What Is a Build Job?

A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.

Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organization folders.

## What is Freestyle Projects ?? 🤔

A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. Here are a few tasks that you could complete when working with a freestyle project in Jenkins:

# Task-01

**create an agent for your app. ( which you deployed from docker in the earlier task)**

* There are a few steps to creating an agent for an application.
    
* first of all, launch the AWS EC2 instance Jenkins Server
    
* now connect the terminal with the SSH key.
    
* Now go to the Jenkins master server and install the required package for a run to the Jenkins master. click here how to install [Jenkins](https://akashblogs-1689395803240.hashnode.dev/day-22-getting-started-with-jenkins)
    

1. Now Go to Jenkins dashboard and click on the manage Jenkins and set agent
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692718565660/ae97d7e5-6f52-4b8f-940c-a551dcf80ea2.png align="center")

1. Now click on Give the node name and click on Permanent click on Create.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734016518/d7cfb273-8c82-4b92-8b54-e11067c215b4.png align="center")
    
2. Now provide your remote directory location where you want to store the files
    
3. node-todo-agent is created
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734228560/bd06a097-e8cc-4105-b482-fd61546c21e2.png align="center")
    
    1. now create a freestyle project
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734526414/6c9577be-512f-414b-bced-690749010e33.png align="center")
        
    2. Now give the url github where from you want pull the code
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734621686/1577633b-4e04-474d-abef-872d4bd4bec9.png align="center")
        
    3. now shell script to build the docker and the docker
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734671476/ce0f1c3e-ac38-4471-a266-c5e4bd6170b5.png align="center")
        
        1. click on save and build now.
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692734727796/1b9f9808-8553-40d6-a788-b3e54611d73c.png align="center")
            
            ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735398934/c527e93f-e0ba-4b3d-a281-35579807add9.png align="center")
            
        2. access this app by using url with exposed port
            
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735518649/b8b11fe1-3262-4ff0-a4dd-7d017e364322.png align="center")
        

# Task-02

* Create Jenkins project to run "docker-compose up -d" command to start the multiple containers defined in the compose file (Hint- use day-19 Application & Database docker-compose file)
    

Go to the jenkins dashboard and click on new iteam and create freestyle project with the description.

1. now give the remote directory url
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735844695/7e10ea2b-8a78-4b58-8f4b-20ee5e859dd5.png align="center")
    
2. now give the soucre code management url
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735865702/eab9bba9-d65c-466f-b5c3-7a6706670f70.png align="center")

1. now click on build steps with shell script and write the script for docker compose.
    
2. click on save and build now.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692736194972/a325d12f-e5d8-446e-9c8d-49e71f0cfeaa.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692736265534/38797138-2002-4862-b04d-bd4b52768102.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735398934/c527e93f-e0ba-4b3d-a281-35579807add9.png align="left")
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692161821862/1401d1ff-c8e9-4729-b6df-106ccc54d7fb.png?auto=compress,format&format=webp align="left")
    
    Set up a cleanup step in the Jenkins project to run the "docker-compose down" command to stop and remove the containers defined in the compose file.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692162254596/325fedcf-547e-4be2-a6a3-41392b2e0b67.png?auto=compress,format&format=webp align="left")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692735398934/c527e93f-e0ba-4b3d-a281-35579807add9.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692162528197/c84d54f7-ab17-48af-a458-46e832458d30.png?auto=compress,format&format=webp align="left")

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)