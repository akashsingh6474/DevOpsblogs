---
title: "Day 73 - Grafana -Setup  🔥"
datePublished: Mon Feb 05 2024 19:15:10 GMT+0000 (Coordinated Universal Time)
cuid: cls9bag4500000al4hhvo9gtn
slug: day-73-grafana-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707160351889/0e57fb55-78a3-4f84-adef-5da0beff77bc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707160452894/0e36d95a-8e89-4dba-8dfb-8ca164612530.png
tags: cloud, aws, devops, grafana, 90daysofdevops, grafana-monitoring

---

Hope you are now clear with the basics of grafana, like why we use, where we use, what can we do with this and so on.

Now, let's do some practical stuff.

In this section, we delve into the comprehensive process of deploying Grafana within an AWS EC2 instance. Grafana stands as an essential data visualization and monitoring tool, pivotal for interpreting and managing diverse datasets. Our guide offers a step-by-step walkthrough, allowing users to harness the potential of Grafana’s user-friendly interface for creating insightful dashboards and analyzing metrics effectively.

### **Task:**

### **Setup Grafana in your local environment on AWS EC2.**

* Go to the AWS console and Launch an EC2 instance for Grafana.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707154866650/a101f188-3b44-44b6-82ba-414ba018488e.png align="center")
    
      Now, allow the inbound port 3000 from the “Security Group”.
    
    Now, take the ssh console and login into the machine.
    
    Download the GPG keys and add them to the trusted keys list.
    
* “wget -q -O - [https://packages.grafana.com/gpg.key](https://packages.grafana.com/gpg.key) | sudo apt-key add”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707155352789/8920f1df-b4af-4f2d-87c7-6674d0bfdcf0.png align="center")
    
     Now, add it to the Grafana repository.
    
* “sudo add-apt-repository "deb [https://packages.grafana.com/oss/deb](https://packages.grafana.com/oss/deb) stable main"”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707155507941/68c4c954-e435-4111-aa02-9bd377c5ff2a.png align="center")
    
      
     Once it has been added, we need to update the system.
    
* sudo apt-get update
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707155586608/6fcfb2a7-6690-4d21-bc45-8f28c8355bdd.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707155600807/d74f0b95-1a3e-47a4-95dc-c7dafb5b4242.png align="center")
    
       Now, we need to install the Grafana.
    
* “sudo apt install grafana”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707155675885/b8702227-2ec5-4005-91ce-ad024f48fe8c.png align="center")
    
     After installation, add Grafana to auto-start and start the Grafana daemon itself.
    
* “sudo systemctl enable grafana-server”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707158575621/6a860995-f77d-45ff-83d1-5c561a197ff7.png align="center")
    
      
    “sudo systemctl start grafana-server”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707158546228/1e4c07d9-4c24-4ef4-b83d-a11987e4d284.png align="center")
    
    The installation of the Grafana repo is finished and ready to use.
    
    Now, check the status. As
    
    “sudo systemctl status grafana-server”
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707158688988/e029da61-4a98-4fd6-b2cc-b16a3bbb0d01.png align="center")
    
      
    Now, goto the browser and search with,
    
    “&lt;IP\_of\_EC2:3000&gt;”
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707159030602/42a47119-59a0-449b-9355-a2b715440b30.png align="center")
    
    Use,
    
    Username: admin
    
    Password: admin
    
      
    after default login you can change your Grafana password or skip password
    
* You will be entered in the Garfana dashboard.
    
* ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707159247634/d2cb8b0f-a2eb-4eec-ace7-0bb5951e9f4e.png align="center")
    
    # **📌Conclusion**
    
    In this session, we covered setup of Grafana server
    
* Hope you found this helpful.
    
    Embrace the challenges ahead and stay excited for continued growth and learning!So I encourage you to try this on your own and let me know in the comment section about your learning experience
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com) **/**[**akashsinghtech40@gmail.com**](mailto:akashsinghtech40@gmail.com)