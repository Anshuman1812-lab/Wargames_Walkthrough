# Bandit Level 5 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-d81f6ca938dd***

![image](https://github.com/user-attachments/assets/805b3a65-383c-4d1e-b152-1e25cfeee08c)

## Level Overview
***Bandit Level 5:** https://overthewire.org/wargames/bandit/bandit5.html*

***Goal:** Locate the password for Level 5, stored in the only human-readable file within the inhere directory.*

***SSH:** ssh bandit4@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit4*

***Password:** 2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ*

![image](https://github.com/user-attachments/assets/83e3576a-59d4-4890-88d7-6e29c64bd4c4)

## Solution
1. **Navigate to the inhere Directory:**
   
Change to the `inhere` directory to access its contents:

![image](https://github.com/user-attachments/assets/aa36c54c-8c18-4f0a-b28e-84a7c556192f)

2. **Identify the Human-Readable File:**
   
List the contents of the directory. Use the `file` command to examine each file (use `*` to examine all the files of the directory at once) and identify the one that is human-readable. Run:

```bash
file ./*
```
![image](https://github.com/user-attachments/assets/98dc227f-6dba-43cb-a17b-c5bafb48a032)

This command will display a list of files with details about each file type. Look for a file labeled as `ASCII text` or `human-readable text`.

3. **Read the Human-Readable File:**
   
Once you’ve identified the human-readable file, use `cat` to display its contents. Since the filenames begin with `-`, the shell interprets it as an option flag. Instead, run:

```bash
cat ./-file07
```
![image](https://github.com/user-attachments/assets/df7b4cd1-3127-4039-843c-8f234f0ee5e9)

The output will contain the password for the next level.
