---
title: "Basic Linux Commands"
datePublished: Mon Jul 17 2023 17:54:37 GMT+0000 (Coordinated Universal Time)
cuid: clk760xp2000209laaud1bilr
slug: basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689616392667/2094e8ab-156e-4e92-be8c-7e3086983449.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689616372168/17f39a09-1daa-437a-a3ec-7a697566423f.jpeg
tags: cloud, aws, devops, devops-journey, 90daysofdevops

---

🔑Key Features:-

🙋‍♂️Introduction:

🪟Viewing the content of a file:

🔒Changing the access permissions of files:

📜Checking the command history

🗑️Removing a directory/folder.

🍉Creating and viewing the content of fruits.txt:

➕Adding content to fruits.txt (One fruit per line)

↗️Showing the top three fruits from fruits.txt

📉Showing the bottom three fruits from fruits.txt

🟢Creating and viewing the content of Colors.txt

🖇️Adding content to Colors.txt (One color per line)

👨‍💻Finding the difference between fruits.txt and Colors.txt

🎉Conclusion.

### 🙋‍♂️Introduction:

Welcome back to Day 3 of the thrilling **#90DaysOfDevOps** challenge! Today, we’ll explore the wonders of Linux commands, like magical keys unlocking every DevOps engineer’s potential! With these tools, navigating your Linux system becomes as easy as exploring a map.

### **➡️Viewing the content of a file:**

To view the contents of a file, we can use the `cat` command. For example, if we have a file named `test.txt`

```plaintext
ubuntu@ghostip$ cat >test.txt 
hey this is test file
ubuntu@ghostip$ ls
test.txt
ubuntu@ghostip$ cat test.txt
hey this is test file
ubuntu@ghostip$
```

### **➡️Changing the access permissions of files.**

Changing the access permissions of files in Linux is done using the **“chmod”** command, which stands for **“change mode.”**

In Linux, every file has three types of permissions: read (r), write (w), and execute (x).

* **“chmod u+rwx example.txt”** grants read, write, and execute permissions to the file owner.
    
* **“chmod go-r example.txt”** revokes read permission from the group and others.
    

```plaintext
ls -l
total 4
-rw-rw-r-- 1 ubuntu ubuntu 22 Jul 17 16:42 test.txt
chmod u+rwx test.txt
chmod go-r test.txt
```

### **➡️Checking the command history.**

This command is used to check the history.

```plaintext
history
cat test.txt
cat >test.txt
ls
cat test.txt
ls -l
chmod u+rwx
chmod u+rwx test.txt
chmod go-r  test.txt
```

### ➡️Removing a directory/folder.

To remove a directory or folder, we can use the `rmdir` or `rm` command. The `rmdir` command is used specifically to remove empty directories, while the `rm` command can be used to remove directories with contents and files.

```plaintext
ls
datafile
rmdir datafile
```

### **➡️Creating and viewing the content of fruits.txt**

The cat command is used to create the file and show the file content.

```plaintext
cat >fruits.txt
cat fruits.txt
```

### ➡️Adding content to fruits.txt (One fruit per line)

To add content to the `fruits.txt` file, we can use either the `vi` or `vim` command.

Using the `vi/vim` command:

```plaintext
ls
fruits.txt
vi fruits.txt 
instert i 
Apple 
Mango 
Banana 
Cherry 
Kiwi 
esc :wq
```

### ➡️Showing the top three fruits from fruits.txt

To show only the top three fruits from the `fruits.txt` file, we can use the `head` command with the `-n` option.

```plaintext
head -3 fruits.txt
Apple 
Mango 
Banana
```

### **➡️Showing the bottom three fruits from fruits.txt**

To show only the bottom three fruits from the `fruits.txt` file, we can use the `tail` command with the `-n` option.

```plaintext
tail -3 fruits.txt
Banana 
Cherry 
Kiwi 
```

### **➡️To create another file Colors.txt and to view the content.**

```plaintext
touch color.txt
```

### ➡️Adding content to Colors.txt (One color per line)

To add content to the `Colors.txt` file, we can use either the `vim` or `echo` command.

**Output:**

```plaintext
vi color.txt
red
yellow
black
white
orange
```

### **➡️Finding the difference between fruits.txt and Colors.txt**

To find the difference between the contents of two files, such as `fruits.txt` and `Colors.txt`, we can use the `diff` command. For example:

This command will display the differences between the two files, if any.

**Output:**

```plaintext
diff fruits.txt color.txt
1,5c1,5
< Apple 
< Mango 
< Banana 
< Cherry 
< Kiwi
---
> red
> yellow
> black
> white
> orange
```

### 📍**Conclusion**

These are just a few of the most important basic Linux commands. There are many other commands that you can learn, but these will give you a good foundation for working with Linux.

I encourage you to practice using these commands so that you can become comfortable with them. The more you use them, the easier they will become.🚀

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

linkedin: [**https://www.linkedin.com/in/akash-singh-48689a176/**](https://www.linkedin.com/in/akash-singh-48689a176/)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)