---
title: "Day-22 : Getting Started with Jenkins 😃"
datePublished: Sat Aug 19 2023 21:49:35 GMT+0000 (Coordinated Universal Time)
cuid: cllijy7ol000b0al0310tg33v
slug: day-22-getting-started-with-jenkins
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692621438083/71508ccc-6ccc-4d4d-957b-3ba3a66b18da.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692481292855/1ace59cd-b9f1-4fec-93ec-2fc3fceb2a8a.png
tags: devops, jenkins, cicd, 2articles1week, 90daysofdevops

---

## 🍽️What is Jenkins?

Jenkins is an open-source project written in Java that runs on Windows, macOS and other Unix-like O.S. It is a free community supported and might be your first choice tool for CI(continuous Integration).

Jenkins automation the entire software deployment life cycle.

Jenkins was originally developed by Sun Microsystem in 2004 under the name Hudson.

it can run on any major platform without any compatibility issues.

Jenkins achieves Continuous Integration with the help of plugins. Plugins allow the integration of Various DevOps stages. If you want to integrate a particular tool, you need to install the plugins for that tool. For example Git, Maven 2 project, Amazon EC2, HTML publisher etc.

Jenkins came into the picture to address the challenges in software development, such as `repetitive tasks,` `manual interventions`, and `inconsistent build and deployment processes`.  
As software projects grew in complexity, manual tasks like `building`, `testing`, and `deploying code` became time-consuming and `error-prone`. Its flexibility, extensibility, and ability to integrate with various tools made it a popular choice for teams seeking to improve their development workflows and deliver software faster and with higher quality.  
Jenkins emerged as an open-source solution that offered developers a way to `automate tasks`, `integrate different tools`, and `establish continuous integration and continuous delivery (CI/CD) pipelines.` This helped teams achieve faster development cycles, better collaboration, and more reliable software releases.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692480206388/76081d3a-8edb-4160-af53-b6dfe491a968.gif align="center")

### **Continuous Integration:**

Continuous integration is a procedure to integrate all the code changes done by several developers in one project. A code is repeatedly tested after a commit to guarantee the code is error and bug-free.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692029141039/e3265944-e9a8-4387-a036-e5eca3838fa7.png?auto=compress,format&format=webp align="left")

### **Continuous Deployment:**

Continuous Deployment aims at continuously releasing the code changes into the production environment.

![Continuous deployment | Atlassian](https://wac-cdn.atlassian.com/dam/jcr:1ebe6373-ebd0-46f4-9b76-791ea2be9d56/cd-diagram@2x.png?cdnVersion=1156 align="left")

### **🚚Continuous Delivery:**

Continuous Delivery is a software engineering practice where the code changes are prepared to be released.

![Understanding Continuous Delivery | TeamCity CI/CD Guide | JetBrains](https://www.jetbrains.com/teamcity/ci-cd-guide/img/Understanding_Continuous-Delivery.svg align="center")

### **Tasks**:

**Create a freestyle pipeline to print "Hello World!!**

Follow a few steps to create a freestyle pipeline

1. first of all create an EC2 - instance Jenkin-server
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692031071640/a79ad58f-7eca-4e1e-9e86-ac3a759008c0.png?auto=compress,format&format=webp align="left")
    
2. install Jenkins on your Ubuntu server by following the link:
    

[**https://www.jenkins.io/doc/book/installing/linux/**](https://www.jenkins.io/doc/book/installing/linux/)

To install Jenkins copy this code to your Ubuntu machine

```bash
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt-get update
sudo apt-get install jenkins
```

1. Now install Java on your machine.
    

```bash
sudo apt update
sudo apt install openjdk-17-jre
java -version
openjdk version "17.0.7" 2023-04-18
OpenJDK Runtime Environment (build 17.0.7+7-Debian-1deb11u1)
OpenJDK 64-Bit Server VM (build 17.0.7+7-Debian-1deb11u1, mixed mode, sharing)
```

* Start Jenkins service - <mark>systemctl start jenkins</mark>
    
* Enable port 8080 on your ec2 instance and access the URL to get the Jenkins UI page
    
* Log in using the **username admin** and to get the **initial admin password** go to this location on your Jenkins server created on ec2 and run the command:
    
* <mark>sudo cd /var/lib/jenkins/secrets/initial admin password</mark>
    
* Copy the password and paste it to the URL page at the Administrator password options below
    
* Copy the password and paste it to the URL page at the Administrator password options below
    
    ![How to Install and configure the Jenkins on Ubuntu 22.04](https://linuxhint.com/wp-content/uploads/2022/04/How-to-Install-and-configure-the-Jenkins-on-Ubuntu-22.04-15.png align="left")
    

Once you unlock Jenkins, customize and prepare the Jenkins environment:

1\. Click the **Install suggested plugins** button to have Jenkins automatically install the most frequently used plugins.

![Selecting the Install suggested plugins option](https://phoenixnap.com/kb/wp-content/uploads/2021/11/install-jenkins-windows-13-install-plugins.png align="left")

2\. After Jenkins finishes installing the plugins, enter the required information on the **Create First Admin User** page. Click **Save and Continue** to Proceed.

![Adding a new administrator user](https://phoenixnap.com/kb/wp-content/uploads/2021/11/install-jenkins-windows-14-create-user.png align="left")

3\. On the **Instance Configuration** page, confirm the port number you want Jenkins to use and click **Save and Finish** to finish the initial customization.

![Verifying the port number for Jenkins](https://phoenixnap.com/kb/wp-content/uploads/2021/11/install-jenkins-windows-15-confirm-port.png align="left")

4\. Click the **Start using Jenkins** button to move to the Jenkins dashboard.

5\. Using the Jenkins dashboard, click **Create New Item**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692032668678/f88e05a8-aca2-45f2-a846-0be5ca78b44a.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692032985932/b98fc7cc-205a-4acb-9e87-554020fe5a91.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692479254796/018d6e0a-387f-40ee-a59b-3e00b8bf4c34.png align="center")

Click on save and build Now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692479627441/c7c6b29a-ae81-44ab-9140-9334cd0d7b79.png align="center")

See the console output once the build is triggered, click on the build number to view the console output of the echo command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692479738619/85a15dc2-32af-4547-a178-85404e740e1b.png align="center")

### **📍Conclusion:**

Jenkins is an open source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.

Jenkins is a tool that is used for automation, and it is an open-source server that allows all the developers to build, test and deploy software. It works or runs on java as it is written in java. By using Jenkins we can make a continuous integration of projects(jobs) or end-to-endpoint automation.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)