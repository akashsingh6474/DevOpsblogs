---
title: "Day 54: Understanding Infrastructure as Code and Configuration Management"
datePublished: Mon Dec 04 2023 13:42:43 GMT+0000 (Coordinated Universal Time)
cuid: clpqyo9fq000d09jlcc8u0mxm
slug: day-54-understanding-infrastructure-as-code-and-configuration-management
tags: cloud, aws, automation, devops, serverless, terraform, 90daysofdevops

---

### **Task:01**

### **What is IAC (Infrastructure -As-Code)?**

When you think about IaC, think about it like this - IaC creates the *thing*.

When you need to create a service in the cloud, a virtualized server, or even a scalable orchestration solution like Kubernetes, you need to think about how to automate it. No one wants to create anything manually anymore and for good reason. There's no way to make manual efforts repeatable and clicking around a UI isn't an efficient way to spend an engineer's time. Because of that, everyone is thinking about how to automate the creation of services, platforms, and systems.

Infrastructure-as-Code is used to automatically create any service or system in the cloud or on-prem with code. The code is typically a provisioning language, like JSON or YAML. However, that's changing rapidly with HashiCorp Configuration Language (HCL), which is a much easier and human-readable language compared to JSON and YAML to write infrastructure code. Another huge concept becoming popular is Infrastructure-as-Software, which is defining your infrastructure with a general-purpose programming language like Python or Go.

The key differentiator between Infrastructure-as-Code and the manual way of creating systems and services is that it's done by writing code. If you're not a developer, that's perfectly fine. A lot of the IaC tools are geared towards non-developers to help them get up to speed. That's why HCL is so human-readable compared to standard programming languages.

You may also hear IaC called Provisioning, as in a provisioning tool. The two phrases are both valid and you'll hear one or the other used depending on who you're talking to.

## What is Configuration Management?

When you think about ConfigMgmt, think about it like this - ConfigMgmt configures the *thing*.

Several years back, virtualization hit the world. A lot of folks didn't think it would end up being as big as it was, but it ended up sweeping the tech nation. Everyone was trying to get on board with VMWare and Hyper-V to get a bigger bang for their buck when it came to servers. Even though creating servers and systems was easier with virtualization, there was still one problem; everything was manual. You had to click around a GUI to provision servers and then you had to RDP or SSH into the servers to configure them. Configuration could consist of starting services, installing dependencies, installing applications, running updates, and much more, so it was a lot of manual effort.

A few companies saw this problem and decided to make a type of tool to automate these tasks. The tool was Configuration Management.

Configuration Management is a way to configure servers. The configuration could be:

* Installing applications
    
* Ensuring services are stopped or started
    
* Installing updates
    
* Opening up ports
    

And much, much more.

You may be thinking to yourself *well why can't ConfigMgmt be used for IaC?*

The answer is - it can. Realistically and technically, you can use ConfigMgmt for IaC. The biggest problem is configuration drift.

Configuration drift is when someone automates a deployment with say, ConfigMgmt, and a person goes into the server and changes the config. No one will know and there isn't an actual blocker to stop the person from doing that.

With IaC tools like Terraform, it's different because Terraform has State files that essentially tell the server *this is how you're supposed to look. Don't change for anyone.*

### **What are the most common IaC and Config Management Tools?**

there are several Infrastructures as Code (IaC) and configuration management tools that are widely used in the industry.

some of the most common IaC and configuration management tools include:

1. **Terraform:**
    
    * Description: Terraform is an open-source IaC tool developed by HashiCorp. It supports multiple cloud providers and on-premises infrastructure.
        
2. **Ansible:**
    
    * Description: Ansible is an open-source automation tool that is often used for configuration management, application deployment, and task automation. It uses declarative language and doesn't require agents on managed nodes.
        
3. **Chef:**
    
    * Description: Chef is a configuration management tool that uses a Ruby-based DSL (Domain-Specific Language) for writing configurations. It is used for automating the deployment and management of infrastructure.
        
4. **Puppet:**
    
    * Description: Puppet is another popular configuration management tool. It uses declarative language to define system configurations and ensure consistency across different systems.
        
5. **AWS CloudFormation:**
    
    * Description: AWS CloudFormation is a native IaC tool provided by Amazon Web Services. It allows you to define and provision AWS infrastructure using a JSON or YAML template.
        
6. **Azure Resource Manager (ARM) Templates:**
    
    * Description: Similar to AWS CloudFormation, Azure Resource Manager allows you to define and deploy Azure infrastructure using JSON templates.
        
7. **Google Cloud Deployment Manager:**
    
    * Description: Google Cloud Deployment Manager is Google's IaC solution. It enables the creation and management of Google Cloud resources using configuration files written in YAML or Python.
        

If you have questions or experiences to share, please feel free to comment below. You can also connect with me on LinkedIn; my name there is Akash Singh. I'm open to suggestions and corrections to improve my blog.

#Day54 #90daysofdevops

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)**/**[**akashsinghtech9@gmail.com**](mailto:akashsinghtech9@gmail.com)