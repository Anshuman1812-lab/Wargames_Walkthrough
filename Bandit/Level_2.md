# Bandit Level 2 Walkthrough
***(https://medium.com/@anshumansingh_71873/overthewire-wargames-88db005be0d4)***

![image](https://github.com/user-attachments/assets/982a09dd-13d4-4f3d-9333-35f2949b488f)

## Level Overview
***Bandit Level 2:** https://overthewire.org/wargames/bandit/bandit2.html*

***Goal:** Retrieve the password for Level 2, stored in a file named - (dash) in the home directory.*

***SSH:** ssh bandit1@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit1*

***Password:** ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If*

![image](https://github.com/user-attachments/assets/34ebda27-24ef-423e-a850-fc4109b95572)

## Solution
1. **List Files in the Home Directory:**

First, use `ls` to list the contents of the home directory and locate the `-` file:

![image](https://github.com/user-attachments/assets/b3acfaa3-28ab-4e51-897a-dd28f4419b65)

This will confirm that `-` is indeed the name of a file in this directory.

2. **Read the Contents of the `-` File:**

Since `-` is often interpreted as an option flag by Linux commands, `cat -` would try to read from standard input rather than the file. To handle this, use `./-`, which specifies the file’s relative path:

![image](https://github.com/user-attachments/assets/1e22e7f5-47f0-4e04-a6aa-485ba66a2e4a)

The `./` prefix tells the terminal explicitly that `-` is a file in the current directory, allowing `cat` to treat it as a filename instead of an option.

3. **Alternative Solution:**
   
If `./-` doesn’t work in certain setups, another approach is to use the full path:

```bash
cat /home/bandit1/-
```
![image](https://github.com/user-attachments/assets/77b3aec1-236c-4c0b-95cb-c50c57fc9de3)

This specifies the absolute path, which can also avoid misinterpretation of `-`.
