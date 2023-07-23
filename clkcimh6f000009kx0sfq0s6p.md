---
title: "File Permissions and Access Control Lists"
seoDescription: "In this blog we will learn about permissions in Linux which is required to change mode of the file and directory and access the file and learn about ACL"
datePublished: Fri Jul 21 2023 11:46:08 GMT+0000 (Coordinated Universal Time)
cuid: clkcimh6f000009kx0sfq0s6p
slug: file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689939668023/9401854a-8487-445e-b17b-1545c32f0cc2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689939803224/456c1e00-4887-400e-8a3e-8cdcbda49f8c.png
tags: linux-file-permissions

---

Welcome Back to my new technical blog on Linux, In this blog we will learn about Linux file permission and change mod of the file owner and many more things Let's get started ..!

### **✍️Introduction.**

In Linux, file permissions are a crucial aspect of the operating system's security model. They determine who can access, modify, or execute files and directories on the system. Understanding and managing file permissions is essential for maintaining the integrity and confidentiality of data and ensuring proper system operation.

File permissions in Linux are represented using a combination of letters and symbols, forming what is commonly known as the "permission string." The permission string consists of ten characters, divided into four parts:

### 📂File Permissions.

File permissions in Linux determine the level of access that the owner, group, and others have for a file or directory. The three digits/alphabets correspond to the permission levels for the owner, group, and others, respectively.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689933309683/fb6beedf-553c-4313-b54a-b57ed2e9f9a7.png align="center")

### 🗃️Access the file Permission using the alphabet.

There are three alphabets to access the files

1\. Read mode (r) it's denoted by r.

2\. Write mode (w) it's denoted by w.

3\. Exctue mode (x) it's denoted by x.

first, create a simple file. after creating the file use the **ls -ltr** command to see the file permissions.

```bash
user@hostip:~$ touch file1
ser@hostip:~$ ls -ltr
```

Output**:**

```bash
-rw-rw-r-- 1 ubuntu ubuntu    0 Jul 21 10:23 file1
```

there is showing some alphabets in the output where **r** means readable, and **w** means we can write any kind of text in the file which means this file is readable and writeable but not there are no permissions to make the executable

let's make this file executable

```bash
chmod u+wx file1
```

### **📂Manage file permission using Numbers.**

File permissions in Linux are represented by a 3-bit system, each bit having a specific meaning:

1. Read (r) - The read permission (bit value of 4) allows a user to view the content of a file or list the contents of a directory.
    
2. Write (w) - The write permission (bit value of 2) allows a user to modify the content of a file or create, delete, and rename files within a directory.
    
3. Execute (x) - The execute permission (bit value of 1) allows a user to run executable files (like scripts or compiled binaries) or access a directory. For directories, the execute permission is required to enter the directory and access its contents.
    

```bash
touch file2
ls -ltr
-rw-rw-r-- 1 ubuntu ubuntu    0 Jul 21 10:37 file2
```

### 👨‍💻chmod.

It is used to change the access mode of the file.

```bash
chmod 700 file2
ls -ltr
-rwx------ 1 ubuntu ubuntu    0 Jul 21 10:37 file2
```

here **\_** is shows the file **rwx** shows the owner/rootuser ------ its other and **1** is for **symbolic link** ubuntu owner ubuntu is for **group** **0** for the file **size in bytes**

### **🧿Chown.**

It is used to change the owner of the file/directory

```bash
mkdir DevOps
touch file3
ls -ltr
drwxrwxr-x 2 ubuntu ubuntu 4096 Jul 21 10:50 DevOps
-rw-rw-r-- 1 ubuntu  ubuntu    0 Jul 21 10:56 file3
```

output.

```bash
sudo chown DevOps file3
ls -ltr
-rw-rw-r-- 1 DevOps  ubuntu    0 Jul 21 10:56 file3
```

Here you will see that the file owner has been changed first it shows Ubuntu but after using the chown its is showing the owner's name is DevOps.

### **🪬Chgrp.**

this command is used to change the group of the file /directory.

```bash
mkdir DevOps
touch file3
ls -ltr
drwxrwxr-x 2 ubuntu ubuntu 4096 Jul 21 10:50 DevOps
-rw-rw-r-- 1 ubuntu  ubuntu    0 Jul 21 10:56 file3
```

output.

```bash
sudo chgrp DevOps file3
ls -ltr
-rw-rw-r-- 1 DevOps  DevoOps  0 Jul 21 10:56 file3
```

Here you will see that the file owner and group have been changed first it shows Ubuntu but after using the chown it is showing the owner's name is DevOps. and the group is also shown as DevOps.

### **🛂Access Control Lists (ACLs).**

Access Control Lists (ACLs) are a more flexible and fine-grained extension to traditional Unix/Linux file permissions. While standard file permissions (user, group, others) provide basic control over access rights, ACLs allow you to grant or deny permissions to specific users or groups for a file or directory.

Using ACLs, you can assign these permissions to specific users or groups separately. For instance, you can grant read and write permissions to one user, read-only access to another user, and no access at all to a third user. The flexibility of ACLs allows for more granular control over file access and better management of shared resources.

`💡getfacl filename`**:** Displays the ACL entries for the specified file or directory.

`💡setfacl -m u:user: permissions filename`: Adds or modifies an ACL entry for a specific user.

```bash
touch file3
getfacl file3
# file: file3
# owner: ubuntu
# group: ubuntu
user::rw-
group::rw-
other::r--
```

Now create one user and assign read-write permission to it,

```bash
sudo useradd akash
setfacl -m u:akash: rw- file3
output:
# file:newfile
# owner: ubuntu
# group: ubuntu
user::---
user:akash:rw-
group::---
mask::rw-
other::-wx
```

### 📍**Conclusion:**

Above mentioned information is much important for a DevOps engineer as he has to manage servers and security. Also if a new member comes into the team, assign appropriate permission to him, and add him to a group.

So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

linkedin: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)