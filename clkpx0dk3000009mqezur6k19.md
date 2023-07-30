---
title: "Day 12 Linux & Git-GitHub Cheat Sheet."
datePublished: Sun Jul 30 2023 20:49:52 GMT+0000 (Coordinated Universal Time)
cuid: clkpx0dk3000009mqezur6k19
slug: day-12-linux-git-github-cheat-sheet
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690750148953/cccd3bc7-4eea-48ed-b1e4-55fa6a5b0942.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690750170458/40256a4f-9ae0-4d2c-a740-a434c23addc8.png
tags: linux, aws, github, git, devops

---

### **🛞Linux commands**

1. ls: List all the directories and files.
    
2. mkdir: Makes a new directory.
    
3. rmdir: Remove a directory (only if it's empty).
    
4. cd: Change directory.
    
5. cd..: Go back to the previous directory.
    
6. pwd: Print the current working directory.
    
7. ls -l: List files with more details.
    
8. cat: Show the content of a file.
    
9. echo: Shows the desired string and value.
    
10. Man: Tells about all commands.
    
11. touch: Create a file.
    
12. cp: Copy files.
    
13. mv: Move files.
    
14. rm: Remove the file permanently.
    
15. sudo: Administrative commands (password).
    
16. head: Display the first 10 lines.
    
17. tail: Display the last 10 lines.
    
18. zip: Zip files in Linux.
    
19. unzip:
    
20. Unzip files in Linux.
    
21. ssh: Secure Shell command in Linux.
    
22. service: Linux command to start and stop services.
    
23. ps: Display active processes.
    
24. wget: Download files from the internet.
    
25. whoami: Show the current user.
    
26. grep: Search for a string within an output.
    
27. sort: Sort the file content.
    
28. cal: View Calendar in the terminal.
    
29. whereis: View the exact location of any command types after this command.
    
30. kill and killall: Kill active processes by process ID or name.
    
31. chmod: Change file permissions.
    
32. chown: Change file ownership.
    
33. history: Shows history of command usage.
    
34. useradd and usermod: Add a new user or change the existing user's data.
    
35. password: Create or update passwords for existing users.
    
36. sudo usermod -a - G create group name username.
    
37. sudo usermod -a - G create group name username.
    
38. This command is used to add a user to a particular group.
    
39. Sudo deluser user groupname This command is used to remove a user from a group.
    
40. get file: This file is used to download ‘file’ from the remote to the local computer.
    
41. quit: This command is used to log out.
    
42. top: This command is used to get the details of all active
    

# **🛞Git-GitHub Commands:**

1. git init: Initialise a local Git Repository
    
2. git add . : Add one or more files to the staging area
    
3. git commit -m “Commit Message” Commit changes to the head but not to the remote repository.
    
4. git status : Check the status of your current repository and list the files you have changed.
    
5. git log : Provides a list of all commits made on a branch
    
6. git diff : View the changes you have made to the file
    
7. git push origin : Push the branch to the remote repository so that others can use it.
    
8. git config --global user.name : “Name” Tell Git who you are by configuring the author name
    
9. git config --global user.email : [user@email.com](mailto:user@email.com) Tell Git who you are by configuring the author email id.
    
10. git clone &lt;repository\_name&gt; : Creates a Git repository copy from a remote source
    
11. git remote add origin : Connect your local repository to the remote server and add the server to be able to push it.
    
12. git branch &lt;branch\_name&gt;: Create a new branch
    
13. git checkout &lt;branch\_name&gt;: Switch from one branch to another.
    
14. git merge &lt;branch\_name&gt;: Merge the branch into the active branch
    
15. git rebase : Reapply commits on top of another base tip
    
16. git checkout -b &lt;branch\_name&gt; : Creates a new branch and switch to it
    
17. git stash : Stash changes into a dirty working directory
    
18. git pull : Update local repository to the newest commit
    
19. git revert &lt;commit\_id&gt; : Revert commit changes
    
20. git clean -n : Shows which files would be removed from the working directory. Use the -f : flag in place of the -n flag to execute the clean.
    
21. git log --summary : View changes (detailed)
    
22. git diff HEAD : Show difference between working directory and last commit.
    
23. git log --oneline : View changes (briefly)
    
24. git reflog : Show a log of changes to the local repository’s HEAD. Add --relative-date flag to show date info or --all to show all refs.
    
25. git rebase -i : Interactively rebase current branch onto . Launches editor to enter commands for how each commit will be transferred to the new base.
    
26. git restore --staged &lt;file\_name&gt; : Resetting a staged file
    
27. git rm -r \[File\_name\] : Remove a file (or folder)
    
28. git config --list : List all variables set in config file, along with their values
    
29. git branch -d &lt;local\_branch&gt; : Delete local branch in Git
    
30. git push -d &lt;remote\_name&gt; &lt;branch\_name&gt; : Delete remote branch in Git
    
31. git stash pop : Unstash the changes
    
32. git commit -am : The -am along with the command is to write the commit message on the command line for already staged files.
    
33. git commit -ammend : The amend is used to edit the last commit. Incase we need to change the last committed message, this command can be used.
    
34. git rm : The git rm command is used to remove or delete files from working tree and index.
    
35. git pull --rebase : Git rebase is used to rewrite commits from one branch to another branch
    
36. git merge --squash : The squash along with git merge produces the working tree. It indexes in the same way as that of the real merge but discards the merge history.
    
37. git revert -e &lt;commit\_id&gt; : edit the commit mesage before reverting, -e is used for the same.
    
38. git blame: git blame is used to know who/which commit is responsible for the latest changes in the repository.
    
39. git cherry-pick: Choosing a commit from one branch and applying it to another is known as cherry-picking in Git.
    

# **📌Conclusion**

In this session, we covered a range of essential Linux and Git-GitHub commands. From navigating directories, managing files, and handling processes in Linux to initializing repositories, creating commits, and collaborating on GitHub, you now have a solid foundation to work effectively in both environments. Keep practicing these commands to become more proficient and efficient in your DevOps endeavors.

Embrace the challenges ahead and stay excited for continued growth and learning!So I encourage you to try this on your own and let me know in the comment section about your learning experience

Thank you for reading!

Thank You! Stay Connected ☁️👩‍💻🌈

Contact me at :

LinkedIn: [**linkedin.com/in/akash-singh-48689a176**](http://linkedin.com/in/akash-singh-48689a176)

E-mail: [**akashsingh6474@gmail.com**](mailto:akashsingh6474@gmail.com) **/**[**akashsinghtech40@gmail.com**](mailto:akashsinghtech40@gmail.com)