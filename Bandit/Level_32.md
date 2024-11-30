# OverTheWire Wargames: Bandit Level 32 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-2720c7cba302***

![image](https://github.com/user-attachments/assets/7abb96ef-13a4-45de-957c-7b2e736c35be)

## Level Overview
***Bandit Level 32:** https://overthewire.org/wargames/bandit/bandit32.html*

***Goal:** There is a git repository at `ssh://bandit31-git@localhost/home/bandit31-git/repo` via the port `2220`. The password for the user `bandit31-git` is the same as for the user `bandit31`.*
*Clone the repository and find the password for the next level.*

***SSH:** ssh bandit31@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit31*

***Password:** fb5S2xb7bRyFmAvQYQGEqsbhVyJqhnDy*

![image](https://github.com/user-attachments/assets/88d344dc-0520-439a-91f6-40f45acd264d)

## Solution
1. **Clone the Repository**
   
As always, start by creating a temporary directory and cloning the repository. Then, move into the cloned repository and analyze the contents.

![image](https://github.com/user-attachments/assets/835dd78b-bb2c-49a8-a65d-c6bd508f8da0)

2. **Check `README.md` Contents**
   
Open `README.md` to check its contents:

![image](https://github.com/user-attachments/assets/24cba506-1fb8-4855-9da0-411451cf0341)

The task is clear: we need to create a file named `key.txt` with the specified content and push it to the `master` branch.

3. **Create the Required File**
   
Create the `key.txt` file with the specified content:

```bash
echo 'May I come in?' > key.txt
```

Verify its contents.

![image](https://github.com/user-attachments/assets/72f26b80-390e-4355-a13a-f796e6f4ffbc)

4. **Handle `.gitignore`**
   
Check the `.gitignore` file to understand why `key.txt` cannot be added normally:

![image](https://github.com/user-attachments/assets/db70be58-9c74-414d-85ca-f12284a1485e)

The `.gitignore` file specifies that all files ending in `.txt` should be ignored. To bypass this, remove the `.gitignore` file and then use `git add` to add `key.txt`. Then, commit the changes to the repository with a message like `Hello` and save:

![image](https://github.com/user-attachments/assets/77a38ebc-d513-4f2b-94ed-f037c38d85fb)

5. **Retrieve the Password**
   
During the push, the repository validates the file and reveals the password for the next level.

![image](https://github.com/user-attachments/assets/eee281fc-b5df-4d66-85da-9586a6263b7d)
