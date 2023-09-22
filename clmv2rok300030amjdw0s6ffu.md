---
title: "Day 28  Jenkins Master & Agents"
datePublished: Fri Sep 22 2023 20:49:19 GMT+0000 (Coordinated Universal Time)
cuid: clmv2rok300030amjdw0s6ffu
slug: day-28-jenkins-master-agents
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695415746886/e66ef728-d1a3-4691-a8ab-557c290b74f6.png
tags: cicd-cjy1vtdk2005kjjs17n8couc3, devops-articles, jenkins-devops, 90daysofdevops

---

# What is Jenkins Master (Server):

![Jenkins Configure Master and Slave Nodes | Medium](https://miro.medium.com/v2/resize:fit:526/0*VPFW83hEmFs_oSSh align="center")

In Jenkins, a "master" refers to the central server in a Jenkins automation setup. It is the core component responsible for managing and coordinating the entire Jenkins environment. The master server:

1. Manages jobs: It schedules and executes jobs or tasks as defined in Jenkins pipelines and projects.
    
2. Distributes work: If configured with multiple agents or nodes, the master distributes tasks to these agents for parallel execution.
    
3. Provides the web interface: The Jenkins master hosts the web-based user interface where users can configure jobs, view build results, and manage Jenkins settings.
    
4. Controls security: It manages user authentication, authorization, and access control for Jenkins.
    
5. Logs and monitors: The master records build logs and provide monitoring and reporting capabilities for the entire Jenkins system.
    

# What is Jenkins Agent?

![Day 28 Task: Jenkins Agents](https://media.licdn.com/dms/image/D5612AQEe_Dr85qfUjg/article-cover_image-shrink_600_2000/0/1679232147261?e=2147483647&v=beta&t=5Q50c1dFbGCjCTPD5J7dMtAGUw2amVlP0KTwBJ88yYU align="center")

In Jenkins, an "agent" (also known as a "node" or "slave") is a worker machine that carries out tasks and builds as directed by the Jenkins master. Agents are used to distribute and parallelize work in Jenkins automation pipelines. Here's what agents do:

1. **Execution of Jobs:** Agents are responsible for executing jobs or tasks that are defined in Jenkins pipelines or projects. When a job is scheduled for execution, the master assigns it to an available agent.
    
2. **Parallelization:** Agents allow Jenkins to perform multiple tasks concurrently. For example, if you have several builds or tests to run, each can be assigned to a separate agent, speeding up the overall process.
    
3. **Diversity of Environments:** Agents can run on different machines with various operating systems, software configurations, and hardware specifications. This allows Jenkins to support a wide range of build and test environments.
    
4. **Isolation:** Agents provide isolation between different builds or jobs. This isolation ensures that one failing build or job doesn't affect others running on different agents.
    
5. **Scalability:** Jenkins can be set up with multiple agents, allowing you to scale your automation infrastructure as needed. You can add or remove agents to handle varying workloads.
    

### **Tasks:**

* **Create an agent by setting up a node on Jenkins**
    
* **step1**: Launch two EC2 instances to serve as the primary **"Master"** and **"Agent."**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695411059013/5a03170f-f966-4d60-82cb-040630013737.png align="center")
    
    **Step 2: Generate SSH keys on the “Jenkins-master” EC2 instance**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695411186552/3d781e9d-14ff-4837-b677-6c420304d0d7.png align="center")
    
    **Step 3: Add public key from “Jenkins-master” instance to “Jenkins-agent” instance under location “.ssh/authorized\_keys”**
    
* **Jenkins-master instance:**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695411384332/326cf55e-c2e0-40f3-ac85-5f5539652259.png align="center")
    
    **Jenkins-agent instance:**
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695412320719/0558b275-1b8c-48de-9546-1ec45d049de2.png align="center")
    

**Step 4: Establish an agent by configuring a node within Jenkins**

* Start by accessing the Jenkins dashboard and select "Manage Jenkins."
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010375088/5cdf8b58-f43c-4518-bb0d-41be92801828.png?auto=compress,format&format=webp align="center")
    
* Next, click on "Manage Nodes and Clouds."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010414925/984e3285-a0d6-4fa2-8d1b-c7ac8faebba2.png?auto=compress,format&format=webp align="left")
    
    step 7: Click on new-Node.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010484127/e9ee1f1e-83c2-4068-afa4-b2697be6fab0.png?auto=compress,format&format=webp align="center")
    

step 8: Add details to add second node, accordingly.\\

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010539139/148bbcbb-9076-472f-b6e8-eaf062858c31.png?auto=compress,format&format=webp align="left")

step 9: Add Credentials &gt;&gt; kind: SSH with private\_key & enter the details accordingly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010922041/ae4b63aa-17c6-4b78-a7a1-e33e5e70be19.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010947091/98ca01cb-2bc3-4491-854c-e1e03bf8452f.png?auto=compress,format&format=webp align="left")

step 10: To enter the private\_key, In Jenkin-Master:

```plaintext
cd /home/ubuntu/.ssh/
ls
cat id_rsa
copy private key
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693010985694/2dd6f377-fab9-40e4-bf1b-7cdf376995c5.png?auto=compress,format&format=webp align="left")

Copy & Paste the Private\_key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011003320/5682b35d-6387-4d3b-917a-8c13784f2f01.png?auto=compress,format&format=webp align="left")

step 11: Connection is Successfull

# **Task-02**

* Run your previous Jobs (which you built on Day 26, and Day 27) on the new agent
    
* Use labels for the agent, your master server should trigger builds for the agent server.
    

step 12: Now build a job, here **restrict the job to the particular agent.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011643254/fcea3cd1-1061-4bde-96ae-fa1aef749353.png?auto=compress,format&format=webp align="left")

step 13: Build Now

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011595598/84eda24d-daae-4ac1-aa2a-4086d2fef45c.png?auto=compress,format&format=webp align="left")

**Output** :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693011773627/b59b4cef-27bb-4a50-be48-478c8883b55a.png?auto=compress,format&format=webp align="left")

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading! Your support means the world to me. Let's keep learning, growing, and making a positive impact in the tech world together.

Happy Learning 😊🙌

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**Akash Singh**](https://in.linkedin.com/in/akash-singh-70o?trk=profile-badge)

[**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)