---
title: "Basic Linux Shell Scripting for DevOps Engineers."
datePublished: Tue Jul 18 2023 19:34:33 GMT+0000 (Coordinated Universal Time)
cuid: clk8p1aoo000409l17cdb9ens
slug: basic-linux-shell-scripting-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689708684001/61113764-07de-42cf-b662-83ec343e862a.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1689709322436/7a72ac12-f43e-40a5-999f-161c2018155e.jpeg
tags: linux, devops, shell-script, 90daysofdevops, happy-learning

---

🔑Key Features:

🤖Introduction.

👨‍💻What is Kernal in Linux?

🧿What is the shell in Linux?

🐚What is Linux Shell Scripting?

🚮What is `#!/bin/bash?` can we write `#!/bin/sh` as well?

📝Write a Shell Script that prints `I will complete #90DaysOofDevOps challenge`

💭Write a Shell Script to take user input, input from arguments and print the variables.

⚙️Write an Example of If else in Shell Scripting by comparing 2 numbers

🎲Conclusion.

### **💡Introduction.**

Welcome to the fourth blog of the "90 Days of DevOps" series! Today, we will dive into the fundamentals of Basic Linux Shell Scripting for DevOps Engineers.

As a DevOps engineer, having a strong understanding of shell scripting is necessary. Shell scripting allows you to automate repetitive tasks, streamline processes, and manage your Linux environment efficiently.

### **✅What is Kernal in Linux?**

The kernel is a computer program that is the core of a computer’s operating system, with complete control over everything in the system.

## ✅What is the shell in Linux?

A shell is a command-line interface (CLI) or a command interpreter that acts as a user interface to interact with an operating system. It is a program that provides a text-based interface for users to enter commands and execute various operations on a computer system.

### **✅What is Linux Shell Scripting?**

shell script is a file containing a series of commands. it read the file and carreis out the command through they have been entered directly on the command line it has the file extension <mark>.sh</mark>

### **✅What is** `#!/bin/bash?` **can we write** `#!/bin/sh` **as well?**

The `#!/bin/bash` or `#!/bin/sh` line At the beginning of a shell script the `#!/bin/bash` or `#!/bin/sh` line is called the shebang or hashbang. It tells the system which interpreter should be used to execute the script.

`#!/bin/bash` indicates that the script should be interpreted and executed using the Bash shell, which is a widely used and powerful shell in Linux. Bash provides additional features and functionalities compared to the standard shell, which makes it a popular choice for scripting in DevOps

Whereas, `#!/bin/sh` specifies the standard shell interpreter. In many systems, this is typically a symbolic link to another shell, often Bash.

### **✅Write a Shell Script that prints** `I will complete the #90DaysOofDevOps challenge.`

To get started, let's try a basic example of a shell script that displays a message. Begin by creating a new file using **vi** editor, such as [**hello.sh**](http://task1.sh) , and include the code provided below:

```plaintext
vi hello.sh
#!/bin/bash
echo "I will complete #90DaysOofDevOps challenge"
esc
:wq
chmod 700 hello.sh
./hello.sh
```

Save the above script in a file with a `.sh` extension, such as `devops_challenge.sh`. Make the file executable by running the following command in the terminal:

### **✅Write a Shell Script to take user input, input from arguments and print the variables.**

```bash
#!/bin/bash
read -p "Welcome! Please enter your name: " name
echo "Hello, $name! How's your DevOps learning is going on?"
```

Save the above script in a file with a `.sh` extension, such as `input.sh`. Make the file executable by running the following command in the terminal:

```bash
chmod + input.sh
```

To execute the script, you can provide the age as an argument:

```bash
./input.sh
```

The script will prompt you to enter your name. After providing it, it will print the entered name and the age provided as an argument.

### **✅Write an Example of If else in Shell Scripting by comparing 2 numbers.**

```bash
#!/bin/bash
read -p "Please enter your name: "age
if [ $age -ge 18 ]; then
  echo "Hello, You can vote."
else
  echo "Hello, You can't vote."
fi
```

### **✅Conclusion.**

In conclusion, shell scripting empowers DevOps professionals to automate, customize, and interact with their Linux systems. With the right knowledge and skills, you can create efficient scripts that save time and enhance productivity. So, embrace the power of shell scripting and unlock new possibilities in your DevOps journey! 🌟💻🚀

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

linkedin: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com)