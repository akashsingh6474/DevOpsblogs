---
title: "Advanced Linux Shell Scripting for DevOps Engineers with User management"
datePublished: Thu Jul 20 2023 05:30:10 GMT+0000 (Coordinated Universal Time)
cuid: clkapr4gw000009jv1k7kemle
slug: advanced-linux-shell-scripting-for-devops-engineers-with-user-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689806350799/dc141d41-e5d9-49f4-ada1-0de68e4de2cc.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689806338580/f262ca70-4b85-42ac-9df0-fcf32e80eec1.png
tags: linux, aws, devops, shell-script, 90daysofdevops

---

### **✅Write a bash script create** [**directories. sh**](http://directories.sh) **that when the script is executed with three given arguments (one is the directory name and second is the start number of directories and the third is the end number of directories ) it creates a specified number of directories with a dynamic directory name.**

```bash
vi createdirectires.sh
#!/bin/bash
eval mkdir $1{$2..$3}
chmod +x createdirectries.sh
./createdirectries.sh day 1 90
```

For creating createDirectories.sh we will use nano editor. Enter the text written above. eval is a Linux command which used to run the arguments as a shell command. Here is how I create and run following commands to create many directories in one script.

We pass 3 command line arguments like directory name starting number and ending number. And this got the result.

### **✅create a Script to backup all your work done till now**

```bash
   #!/bin/bash

# backup directory
backup_dir="/home/ubuntu/scripts/backup"

# timestamp for the backup file name
timestamp=$(date +"%Y%m%d%H%M%S")

# backup file name
backup_file="$backup_dir/work_backup_$timestamp.tar.gz"

# create backup
tar -czf "$backup_file" /home/ubuntu/scripts

echo "Boooom.....Backup created: $backup_file"
```

### **✅Read About Cron and Crontab, to automate the backup Script.**

Cron is a time-based job scheduler in Unix-like operating systems that allows you to schedule and automate the execution of tasks or scripts at specified intervals. Crontab is the configuration file used by Cron to define the schedule and commands to be executed.

30 2 \* /usr/bin/command-to-be-executed

In this example, the cron job is scheduled to run at 2:30 AM every day.

![20 Tips for Scheduling Cron Jobs In Linux: A Beginner's Guide](https://tecadmin.net/wp-content/uploads/2013/03/crontab-2.png align="center")

### **✅About User Management in Linux**

User management in Linux involves creating, modifying, and deleting user accounts and managing user-related settings. Here are some common tasks and tools used for user management in Linux:

\*\*1.Adding a User:  
\*\*The `adduser` or `useradd` command is used to create a new user account. For example: `sudo adduser username`.

```bash
sudo useradd abhinav
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689802857736/2faa0016-baac-4414-a7c2-2b0286d4cc41.png align="center")

```bash
cat /etc/passwd
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689803431514/b5c4de21-1184-4d84-8da3-b6ec2605d2f7.png align="center")

Specify the user's password using the `passwd` command: `sudo passwd username`.

```bash
sudo passwd abhinav
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689803044475/04d8a5e9-a3de-4631-aa95-e3915f133377.png align="center")

To modify a user's password, you can use the `passwd` command: `sudo passwd username.`

**3.Deleting a User:**

The `deluser` or `userdel` command is used to delete a user account. By default, it removes the user's home directory. Example: `sudo deluser username.`

```bash
sudo userdel abhinav
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689803557521/004b3981-a1f6-4a78-ad2f-07db133bfe4c.png align="center")

### **✅Create 2 users and just display their Usernames.**

```bash
sudo useradd ankit
sudo useradd vishal
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689804901991/74f6d3c5-0c94-4db0-b7d9-1b755a3b8599.png align="center")

```bash
awk -F: '{print $1}' /etc/passwd
```

this will create two users in the order to display them .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689805063336/7617c3e7-9714-47f1-a266-b0e8a01af3ca.png align="center")

📍**Conclusion** These are just a few of the most important shell script advane commands. There are many other commands that you can learn, but these will give you a good foundation for working with Linux .

I encourage you to practice using these commands so that you can become comfortable with them. The more you use them, the easier they will become.

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

linkedin: [**https://www.linkedin.com/in/akash-singh-48689a176/**](https://www.linkedin.com/in/akash-singh-48689a176/)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)