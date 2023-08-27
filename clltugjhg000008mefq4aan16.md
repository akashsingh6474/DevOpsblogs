---
title: "Day 25 Complete Jenkins CI/CD Project - Continued with Documentation"
datePublished: Sun Aug 27 2023 19:29:14 GMT+0000 (Coordinated Universal Time)
cuid: clltugjhg000008mefq4aan16
slug: day-25-complete-jenkins-cicd-project-continued-with-documentation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693164928172/2b23367e-7122-40c4-a090-8dc9de8e7cf3.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693164916664/1289421c-4c37-42a9-adfb-e07a9e869698.png
tags: devops, jenkins, ci-cd, 90daysofdevops

---

### **Tasks:**

* **Document the process from cloning the repository to adding webhooks, Deployment, etc. as a README, go through** [**this example**](https://github.com/LondheShubham153/fynd-my-movie/blob/master/README.md)
    
* **A well-written readme file will help others to understand your project and you will understand how to use the project again without any problems.**
    

creating a complete Jenkins CI/CD project with documentation in an extensive process that requires the following steps:

1. **Introduction:** Summary of the project and what's the purpose of the documentation.
    
2. Created the project node-todo-cicd application that is available on GitHub [https://github.com/LondheShubham153/node-todo-cicd](https://github.com/LondheShubham153/node-todo-cicd) is a demonstration of a **Node.js** Web application integrated with CI/CD (Continuous integration and Continuous Deployment) pipeline. This project showcases the automation of the building, testing and deployment of a **Node.js** application using Jenkins pipeline.
    

**Prerequisites:** list of software that should be installed before starting the project.

first installation Jenkins and java then repo. setup

1. Firstly open an AWS account and launch an instance with the Jenkins server name
    
2. and connect the instance with your terminal. with the **SSH key** that was created at that time when you launched your instance. and copy that key.
    
3. Open the terminal and go to download &lt;cd Downloads/&gt; and paste the key.
    
4. Now update your machine and install java
    
5. <mark>#sudo apt update</mark>(for your machine)
    
6. <mark>#sudo apt install openjdk-11-jre</mark>
    
7. Check whether the java is installed or not <mark># java --version</mark>
    
8. If Java is installed then it will show the Java version.
    

**For installation Jenkins.**

1. Follow this command to install Jenkins
    
2. curl -fsSL [https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key](https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key) | sudo tee  
    /usr/share/keyrings/jenkins-keyring.asc &gt; /dev/null echo deb \[signed-by=/usr/share/keyrings/jenkins-keyring.asc\]  
    [https://pkg.jenkins.io/debian-stable](https://pkg.jenkins.io/debian-stable) binary/ | sudo tee  
    /etc/apt/sources.list.d/jenkins.list &gt; /dev/null sudo apt-get update sudo apt-get install jenkins
    
3. Check whether Jenkins is installed or not <mark># jenkins --version</mark>
    
4. Now start the Jenkins #sudo systemclt start jenkins
    

**Unlock the Jenkins:**

1. When you go on the Jenkins web page this will show a path copy that and open in your terminal.
    
2. cat /var/lib/jenkins/secrets/
    
    initialAdminPassword\`\`\`
    
3. Create your username and password.
    

Open your Jenkins dashboard and create a Jenkins job for your CI/CD pipeline.

Enter the name of the job and select the Jenkins freestyle project. and describe the project.

Now give the location of the Code. that you want to deploy an application. automation by the using Jenkins pipeline.

I use this repo. [https://github.com/LondheShubham153/node-todo-cicd](https://github.com/LondheShubham153/node-todo-cicd) to fork and for the creating project

Add the above repo to GitHub projects

and install some plugins on Jenkins for running GitHub and many more types of software.

Give the GitHub URL [https://github.com/akashsingh6474/node-todo-app](https://github.com/akashsingh6474/node-todo-app)

Give the source code management URL where your code is stored.

[https://github.com/akashsingh6474/node-todo-app](https://github.com/akashsingh6474/node-todo-app)

for adding the webhooks trigger for that if your developer did any kind of change to your pipeline with created automatically.

Go to the GitHub repo and click on the setting

Click on webhook and add webhook with your IP address and port where your application will run [http://3.83.213.152:8000](http://3.83.213.152:8000/todo)/github.webhook/ select the 'application/JSON'.

Select the event that should trigger the webhook.

Save the webhook configuration.

Wherever we change and commit the repo it gets a green tick on the webhook configuration.

1. ***Build Stage Configuration: Details on setting up the build stage with the required tools.***
    

* Set up the build stage in your Jenkins job to compile and package your application.
    
* In Execute shell add a command where Groovy syntax while writing the build script.
    
* Ensure that the builds worked successfully.
    
* Where ever we change the code from Git Hub, the webhook will trigger the Jenkins job and starts building automatically.
    

1. ***Test Stage Configuration: Description of integrating automated tests.***
    

* Integrate automated testing in the Jenkins pipeline to ensure code quality.
    

1. ***Deployment Configuration: Explanation of deploying the application.***
    

* Set up deployment to your target environment (e.g., staging, production).
    

1. ***Troubleshooting: Common issues and solutions.***
    
    Make sure in your security group inbound rule add Jenkins default port no. 8080 and application port no. 8000
    
2. ***Conclusion: Wrap-up of the documentation and future improvements.***
    
    By creating a new Jenkins job for your CI/CD pipeline, you automate the entire process from source code management to deployment, ensuring consistent and reliable software delivery. Jenkins orchestrates these steps based on triggers you define, providing a streamlined and efficient workflow for development and deployment.
    

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading! Your support means the world to me. Let's keep learning, growing, and making a positive impact in the tech world together.

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)