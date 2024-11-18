# Bandit Level 1 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-a8999aba43d2***

![image](https://github.com/user-attachments/assets/5c0f6dbd-dc13-4270-acdb-91b684f19d99)

## Level Overview
***Bandit Level 1:** https://overthewire.org/wargames/bandit/bandit1.html*

***Goal:** Retrieve the password for Level 1, which is stored in a file named readme located in the home directory of your Bandit Level 0 session.*

***SSH:** ssh bandit0@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit0*

***Password:** bandit0*

## Solution
1. **Confirm Your Starting Directory:**
   
Upon logging into Bandit Level 0, you’re automatically placed in the home directory. You can confirm this by using the command `pwd`

This command will output the current directory path. You should see something like `/home/bandit0`.

![image](https://github.com/user-attachments/assets/f3202f7e-4623-4a71-9573-735b0d7dbe5f)

2. **List Files in the Home Directory:**
   
To find the `readme` file, list the directory contents with `ls`

This command will display the files and directories in your current location. You should see the readme file in the output.

![image](https://github.com/user-attachments/assets/fb34fa90-c9ef-420c-939c-749e3daa2d15)

3. **Read the `readme` File:**
   
Now that you’ve located the `readme` file, read its contents using the `cat readme` command.

This command will output the file’s contents directly in the terminal, revealing the password for the next level.

![image](https://github.com/user-attachments/assets/edd4500c-0d06-429f-b94c-ad3e00ed939a)
