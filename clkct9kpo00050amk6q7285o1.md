---
title: "📀Understanding Package Manager📀"
datePublished: Fri Jul 21 2023 16:44:02 GMT+0000 (Coordinated Universal Time)
cuid: clkct9kpo00050amk6q7285o1
slug: understanding-package-manager
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689957547844/6641fea9-091b-4d4b-8852-afc60fddbbea.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689957823648/b3e8b7f3-4ed9-45dd-8afc-5bf8e23e0a4f.jpeg
tags: cloud, linux, aws, devops, 90daysofdevops

---

### **Introduction**.

Welcome Back to my new technical blog #90DaysOfDevOps challenge. In this blog, we will learn about package manager and its essential tools like APT (Advanced Package Tool) 🛠️ and YUM (Yellowdog Updater Modified) 🛠️, along with the role of systemctl and system. Our first task will be installing Docker 🐳 and Jenkins 🏗️ using package managers. For Docker installation, we'll set up the repository, while for Jenkins, we'll utilize APT on Ubuntu. Additionally, we'll learn to check the status of the Docker service, stop the Jenkins service, and understand the difference between systemctl and service commands. Let's get started ..!

### ⚙️What is a package?

In Linux, a package typically refers to a compressed archive file that contains software, along with the necessary installation scripts and metadata. Linux distributions often use package management systems to simplify the process of installing, updating, and removing software from the operating system.

### ♾️Different kinds of package managers.

**Advanced Package Tool (APT)**:

APT is used primarily in Debian-based distributions (e.g., Debian, Ubuntu, Linux Mint). It works with `.deb` packages and uses a set of command-line tools like `apt-get`, `apt-cache`, and `aptitude` to manage packages and handle dependencies.

there are the following steps to install the package on the machine

**Yellowdog Updater, Modified (YUM):**

YUM is commonly used in Red Hat-based distributions (e.g., Red Hat Enterprise Linux, CentOS, Fedora). It works with `.rpm Yum commands include that yum install and yum update`

```bash
To install a package: sudo yum install package_name

To update packages: sudo yum update followed by sudo apt-get upgrade

To remove a package: sudo yum remove package_name
```

### **⚙️How we use package manager :**

Package managers are mostly used for installing, updating, configuring, and removing software packages on a computer.

for installing the package on ubuntu.

```bash
sudo apt-get install package_name

```

for updating the software package on Ubuntu.

```bash
To update packages: sudo yum update followed by sudo apt-get upgrade
```

for removing software package from the machine on Ubuntu

```bash
To remove a package: sudo yum remove package_name
```

### **🦈Installation of Docker.io and Jenkins using the package manager:**

install docker on an Ubuntu machine.

```bash
sudo apt install docker.io -y
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689954560656/f0170f02-f5ea-4fcd-83a7-056bf963bfaa.png align="center")

To check the docker version.

```bash
docker --version
Docker version 20.10.21, build 20.10.21-0ubuntu1~22.04.3
```

### **👨‍💻Install Jenkins on ubuntu:**

To install Jenkins on Ubuntu using APT, follow these steps:

1. Jenkins requires **Java** to run, so we'll update the Debian apt repositories, install OpenJDK 17, and check the installation with the commands:
    

```bash
sudo apt update
sudo apt install openjdk-11-jdk
java --version
```

Next, let’s install the Jenkins Long-Term Support release by using the below commands:

```bash
 curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null
 sudo apt-get update
 sudo apt-get install jenkins
```

Start the Jenkins service:

```bash
sudo systemctl start jenkins
```

Enable Jenkins to start on system boot:

```bash
 sudo systemctl enable jenkins
```

Jenkins should now be installed and running on your Ubuntu system. You can access it by opening your web browser and navigating to [`http://localhost:8080`](http://localhost:8080).

### **♾️what are systemctl and systemd**

`systemctl` and `systemd` are core components of modern Linux systems, providing control over system services and managing the boot process. Here's an overview of each:

**systemctl:** `systemctl` is a command-line tool used to control and manage system services in Linux distributions that use `systemd` as their init system (which is the case for most modern distributions). It allows users to start, stop, restart, enable, disable, and view the status of services, among other functions. With `systemctl`, you can interact with both system services and user services.

Commonly used `systemctl` commands include:

* `systemctl start <service_name>`: Starts a service.
    
* `systemctl stop <service_name>`: Stops a service.
    

```bash
user@hostip:~$ sudo systemctl start docker
user@hostip:~$ sudo systemctl status docker
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689956178489/fc5bb201-eb7d-4ed0-ad2f-792f8c35cb42.png align="center")

* `systemctl restart <service_name>`: Restarts a service.
    
* `systemctl enable <service_name>`: Enables a service to start at boot.
    
* `systemctl disable <service_name>`: Disables a service from starting at boot.
    

**systemd:** `systemd` is a system and service manager for Linux operating systems. It serves as the first process (PID 1) and is responsible for initializing the system during the boot process. `systemd` replaces the traditional SysVinit, bringing many improvements, such as parallel service initialization and dependency tracking.

Key features of `systemd` include:

**Service Management**: `systemd` manages the starting, stopping, and monitoring of services, including daemons and user services.

**Unit Files**: Services, sockets, devices, and other system resources are defined by unit files with `.service`, `.socket`, `.device`, etc., extensions. These files contain configuration information for how each unit should be started and managed.

### **♾️Stopping the Jenkins Service.**

```bash
sudo systemctl stop jenkins.
```

### **♾️Difference between systemctl and service♾️**

`systemctl` and `service` are both commands used to manage services in Linux, but they have some differences in their functionality and usage.

`systemctl` is a more modern and 🛸 powerful service management utility introduced with systemd, which is the default init system in many modern Linux distributions.

It has some features for controlling services, including starting, stopping, restarting, enabling (starting at boot), disabling (not starting at boot), and checking the status of services.

**service**:

* `service` is a legacy command used in init-based systems (SysVinit) to manage services.
    
* It is still available in many Linux distributions for backward compatibility but is being phased out in favor of `systemctl`.
    
* `service` provides a simpler interface for starting, stopping, and restarting services, but it has fewer features compared to `systemctl`.
    
    ```bash
    service docker status
    ```
    
    ### **📍Conclusion:**
    
    Above mentioned information is much important for a DevOps engineer as he has software manager updates and some commands on software services and dependencies.
    
    So I encourage you to try this on your own and let me know in the comment section about your learning experience
    
    Thank you for reading!
    
    Thank You! Stay Connected ☁️👩‍💻🌈
    
    Contact me at :
    
    linkedin: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)
    
    E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)