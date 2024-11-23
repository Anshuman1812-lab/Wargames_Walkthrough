# OverTheWire Wargames: Bandit Level 18 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-f8aa077102be***

![image](https://github.com/user-attachments/assets/2f110831-7d86-4358-aed5-68316cce466e)

## Level Overview
***Bandit Level 18:** https://overthewire.org/wargames/bandit/bandit18.html*

***Goal:** The password for Level 18 is located in the file `passwords.new` and is the only line that differs from `passwords.old`. Your task is to find the line that changed between these two files.*

***SSH:** ssh bandit17@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit17*

***Password:** EReVavePLFHtFlFsjn3hyzMlvSuSAcRD*

*OR*

*Private SSH key from the previous level*

![image](https://github.com/user-attachments/assets/c12345f8-04cf-4697-8fb1-b90e7a1a7c9e)

## Solution
1. **List Files in the Home Directory:**
   
Begin by listing the files in the home directory to confirm the presence of `passwords.old` and `passwords.new`:

![image](https://github.com/user-attachments/assets/2bf4efb3-7f04-4f7e-ac25-98fb23b29c29)

2. **Use `diff` to Compare the Files:**
   
Use the `diff` command to compare `passwords.old` and `passwords.new`. This command will output only the lines that differ between the two files:

```bash
diff passwords.old passwords.new
```

The output will include only the line that has changed in `passwords.new`, which is the password for the next level.

![image](https://github.com/user-attachments/assets/17fbb974-4135-47d3-b2bd-250fe182c382)
