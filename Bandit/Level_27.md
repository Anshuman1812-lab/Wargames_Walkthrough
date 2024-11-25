# OverTheWire Wargames: Bandit Level 27 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-ac3be8d0cb99***

![image](https://github.com/user-attachments/assets/2ed49d66-5e41-480d-9036-8882196f6d1c)

##Level Overview
***Bandit Level 27:** https://overthewire.org/wargames/bandit/bandit27.html*

***Goal:** Good job getting a shell! Now hurry and grab the password for bandit27!*

***SSH:** ssh bandit26@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit26*

***Password:** s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ*

![image](https://github.com/user-attachments/assets/b6d61ca0-927f-46be-abb8-1a27f6022dfa)

## Solution
The solution for Bandit level 26 is required for this challenge. The shell we got for `bandit26` is needed to get the password for `bandit27`.

1. **List the Contents of the Home Directory**

After gaining access to the shell for `bandit26`, use the `ls` command to inspect the files in its home directory.

![image](https://github.com/user-attachments/assets/d42892e1-e12e-406c-ad45-a8632c6dabd2)

2. **Analyze the bandit27-do File**

Run the `bandit27-do` file without any arguments to understand what it does:

![image](https://github.com/user-attachments/assets/d420073f-f232-4247-8ff2-9e62282c9ac2)

This tool allows you to execute commands as another user. This is similar to the functionality encountered in [Level 20](https://github.com/Anshuman1812-lab/Wargames_Walkthrough/blob/main/Bandit/Level_20.md).

3. **Retrieve the Password**

Use the `bandit27-do` tool to read the password file for `bandit27`, which is located at `/etc/bandit_pass/bandit27`:

```bash
bandit26@bandit:~$ ./bandit27-do cat /etc/bandit_pass/bandit27
```

The command runs `cat` as the `bandit27` user, which prints the password.

![image](https://github.com/user-attachments/assets/f3da7ad8-8b8a-49ea-8856-4efd3806946f)
