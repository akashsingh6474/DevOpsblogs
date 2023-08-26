---
title: "Day 24 Complete Jenkins CI/CD Project"
datePublished: Sat Aug 26 2023 21:19:51 GMT+0000 (Coordinated Universal Time)
cuid: cllsiyxr5000109mdaf795o6i
slug: day-24-complete-jenkins-cicd-project
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693084658860/1ac04e25-35b0-4371-9a9d-9ad08c3c0599.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1693084778276/46061d83-c96d-4c86-acb2-e7f79608b171.png
tags: devops, jenkins, 2articles1week, ci-cd, 90daysofdevops

---

### **Introduction.**

Hello everyone welcome back to my blog. I hope everyone is doing great and learning new things. It is my day-24 blog in this blog I'll be covering **Jenkins** ci/cd pipeline, building the pipeline with the project and learning about what are **GitHub** integration GitHub **webhooks** and many more things let's start...!

### **GitHub Integration.**

GitHub integration is the process of connecting GitHub with other tools and services to automate tasks, improve communication, and streamline your workflow.

There are many different ways to integrate GitHub. Some popular integrations include:

* **Slack:** This integration allows you to receive notifications about GitHub events in Slack, such as new commits, pull requests, and issues.
    
* **Jira:** This integration allows you to track bugs and issues in Jira from GitHub.
    
* **Confluence:** This integration allows you to create and manage documentation for your GitHub projects in Confluence.
    
* **Bitbucket:** This integration allows you to collaborate on code with team members who use Bitbucket.
    
* **Travis CI:** This integration allows you to automatically run tests and deploy your code when you push changes to GitHub.
    

Here are some of the benefits of using GitHub integration:

* **Automate tasks:** GitHub integration can help you automate tasks, such as running tests, deploying code, and sending notifications. This can save you time and improve your productivity.
    
* **Improve communication:** GitHub integration can help you improve communication with your team by making it easy to share code, discuss changes, and track progress.
    
* **Streamline your workflow:** GitHub integration can help you streamline your workflow by connecting different tools and services. This can make it easier to get things done.
    

Here are some examples of how GitHub integration can be used:

* You can use GitHub integration with Slack to get notified of new commits, pull requests, and issues. This can help you stay up-to-date on the latest changes to your code.
    
* You can use GitHub integration with Jira to track bugs and issues in your code. This can help you keep track of the progress of your development work.
    
* You can use GitHub integration with Confluence to create and manage documentation for your code. This can help you make your code more accessible and understandable to others.
    
* You can use GitHub integration with Bitbucket to collaborate on code with team members who use Bitbucket. This can help you get feedback on your code and improve your development process.
    
* You can use GitHub integration with Travis CI to automatically run tests and deploy your code when you push changes to GitHub. This can help you ensure that your code is always working properly.
    

### **Git webhooks:**

A GitHub webhook is a way to receive notifications from GitHub whenever certain events occur, such as a new commit being pushed to a repository, a pull request being opened, or a new issue being created.

Webhooks are delivered to a URL that you specify. When GitHub sends a webhook, it sends a POST request to the URL with information about the event that occurred.

You can use webhooks to automate tasks, such as:

* Sending notifications to a chat app, such as Slack or Discord.
    
* Triggering a build process.
    
* Updating a database.
    
* Deploying code to a production server.
    

To set up a GitHub webhook, you will need to:

1. Go to the settings page of the repository or organization where you want to create the webhook.
    
2. Click on "Webhooks".
    
3. Click on "Add webhook".
    
4. In the "Payload URL" field, enter the URL where you want to receive the webhook notifications.
    
5. Select the events that you want to be notified about.
    
6. (Optional) Enter a secret. This will help to secure your webhooks.
    
7. Click on "Create webhook".
    

Once you have created a webhook, GitHub will start sending notifications to the URL that you specified.

Here are some of the benefits of using GitHub webhooks:

* They can help you automate tasks, which can save you time and improve your productivity.
    
* They can help you stay up-to-date on the latest changes to your code.
    
* They can help you improve your communication with your team.
    
* They can help you improve your development workflow.
    

### **Tasks**:

* **Fork** [**this**](https://github.com/LondheShubham153/node-todo-cicd.git) **repository:**
    
* **Create a connection to your Jenkins job and your GitHub Repository via GitHub Integration.**
    

**Step:1**

We had already created a node ci-cd app in #Day23 task you can refer to my previous blog [Day-23.](https://akashblogs-1689395803240.hashnode.dev/day-23-jenkins-freestyle-project-for-devops-engineers) From step 2 we can integrate through webhook

**Step:2**

Now to integrate github and Jenkins we need to create Github Webhooks.

Under Build Triggers: Select GitHub hook trigger for Gitscm Polling.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693079469017/3670fc6a-9004-476b-a9e1-f1ff7360628e.png align="center")

**Step 3:**

**Webhooks create the hyperlink between GitHub & Jenkins.**

**Any changes made to the GitHub repo will be automatically identified by Jenkins and will be pushed to the webhook URL.**

**To create Webhook**: Go to **Settings** of your forked GitHub repo.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693079730851/318816b6-0f12-4f41-93d6-face05b9820b.png align="center")

**Step 4:** Click on Add Webhook

[https://karanidnani6.hashnode.dev/day24complete-jenkins-cicd-project](https://karanidnani6.hashnode.dev/day24complete-jenkins-cicd-project)

**Step 5:** After setting up the webhooks do not forget to **refresh the page** unless the **webhook URL is ticked** as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693079978958/ff445b21-8bee-4bef-aac5-a16570323e64.png align="center")

**Step 6**: Now come back to the Jenkins dashboard, click on Build steps &gt; Execute Shell &gt; type the command that will be executed after the job is built & save.

**Step 7**: Now I will make slight changes to the code by adding a comment at the beginning of the docker file. [https://karanidnani6.hashnode.dev/day24complete-jenkins-cicd-project](https://karanidnani6.hashnode.dev/day24complete-jenkins-cicd-project)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693078918906/d0bc2e3d-dba4-484a-9a12-036f11a4d3e0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693080384368/82d24bf3-c361-44af-992d-0ac068240757.png align="center")

**Step 8:** Commit the changes made.

**Step 9:** Exactly after few seconds of the commit made onto the code, the Job in the Jenkins dashboard starts to build automatically.

Tep 18: And the job is successful.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693080793840/71f5b98f-b85c-4b74-8d80-e7511898127c.png align="center")

**Step 10:** You can click on the **Console Output** to view the output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693081245600/d0a94af1-58ad-4039-b554-5ab95c22f42e.png align="center")

# Task-02

* **In the Execute shell run the application using Docker compose**
    
* For Task2 follow the same as the above steps, but **change the execute shell command as below :**
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691993716952/4cebd9a6-dc99-47c7-a7ee-9e433b5344c5.png?auto=compress,format&format=webp&auto=compress,format&format=webp align="left")

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)