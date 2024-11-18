# Bandit Level 4 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-c089d0f7eb18***

![image](https://github.com/user-attachments/assets/c21ac0b7-6eed-47fe-a7a7-5b456ce55f68)

## Level Overview
***Bandit Level 4:** https://overthewire.org/wargames/bandit/bandit4.html*

***Goal:** Locate the password for Level 4, stored in a hidden file inside the inhere directory.*

***SSH:** ssh bandit3@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit3*

***Password:** MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx*

![image](https://github.com/user-attachments/assets/84d0d052-7d0d-4c1e-b386-e7e82e703688)

## Solution
1. **Navigate to the `inhere` Directory:**
   
Start by changing directories to `inhere` using:

![image](https://github.com/user-attachments/assets/3f001f87-ad4d-4852-b67c-b0e0345d7781)

2. **List All Files, Including Hidden Files:**
   
Since the file is hidden, simply listing the directory contents using the `ls` command won’t help. Use the `-a` flag of the `ls` command to list all files, including hidden ones (hidden files in Linux begin with a dot `.`)

![image](https://github.com/user-attachments/assets/ef05eb23-74a2-4c62-9ab0-59352bb6683a)

You should see all the files with names that start with a dot (`.`), indicating they are hidden.

3. **Read the Hidden File’s Contents:**
   
Use `cat` to display the contents of the hidden file.

```bash
cat ...Hiding-From-You
```
![image](https://github.com/user-attachments/assets/4379edda-18d4-4e29-857f-6e38b92c6d99)

The file’s content will contain the password for Level 4.
