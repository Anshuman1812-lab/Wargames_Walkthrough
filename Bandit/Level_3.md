# Bandit Level 3 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-62514f007928***

![image](https://github.com/user-attachments/assets/575ebf7c-a21a-4245-807a-0a48211c7551)

## Level Overview
***Bandit Level 3:** https://overthewire.org/wargames/bandit/bandit3.html*

***Goal:** Retrieve the password for Level 3, stored in a file named spaces in this filename in the home directory.*

***SSH:** ssh bandit2@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit2*

***Password:** 263JGJPfgU6LtdEvgfWU1XP5yac29mFx*

![image](https://github.com/user-attachments/assets/b71d1811-4279-4e9a-a6a3-ca47dbfa7fd8)

## Solution
1. **List Files in the Home Directory:**
   
Begin by listing the directory contents to verify the exact filename:

![image](https://github.com/user-attachments/assets/d6a6533e-4525-419c-a916-a1f043a52095)

You should see the file named spaces in this filename.

2. **Reading the File with Spaces in Its Name:**
   
Similar to the previous level, simply typing `cat spaces in this filename` doesn’t work because the shell interprets each space-separated word as a distinct argument. Here, it sees four separate arguments (`spaces`, `in`, `this`, and `filename`) instead of recognizing them as one filename.

![image](https://github.com/user-attachments/assets/9713572a-acd9-48c6-95e1-de21eb8cb0c6)

To access a filename with spaces, enclose it in quotes to treat the entire name as a single string:

```bash
cat "spaces in this filename"
```
![image](https://github.com/user-attachments/assets/e54eb06d-877c-4fcf-aa41-5964da49159c)

Alternatively, you can use backslashes (`\`) to escape each space:

```bash
cat spaces\ in\ this\ filename
```
![image](https://github.com/user-attachments/assets/e4a59b7c-41d2-411b-a8cd-9c38f7a529fc)

Either approach will output the contents of the file, showing the password for the next level.

