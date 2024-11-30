# OverTheWire Wargames: Bandit Level 28 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-7b7b796ea89a***

![image](https://github.com/user-attachments/assets/1ad9e0af-4fa9-40be-a294-a62c894caf41)

## Level Overview
***Bandit Level 28:** https://overthewire.org/wargames/bandit/bandit28.html*

***Goal:** There is a git repository at `ssh://bandit27-git@localhost/home/bandit27-git/repo` via the port `2220`. The password for the user `bandit27-git` is the same as for the user `bandit27`.*
*Clone the repository and find the password for the next level.*

***SSH:** ssh bandit27@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit27*

***Password:** upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB*

![image](https://github.com/user-attachments/assets/bf8362e4-42c6-43e9-b6f2-45d7718ef2bf)

## Solution
1. **Setting Up the Environment**
   
Before cloning the repository, it’s good practice to create a temporary directory for your work. This keeps your main filesystem clean and organized. On Linux, we can create a temporary directory using the `mktemp -d` command, which automatically generates a unique folder name.

```bash
mktemp -d
```

2. **Cloning the Repository**
   
After creating the directory, navigate to it and clone the Git repository using the provided SSH address. Git will prompt for the password of `bandit27-git`. Simply input the current level’s password when asked.

```bash
git clone ssh://bandit27-git@localhost:2220/home/bandit27-git/repo
```

Make sure you add the port number `localhost:2220` to the git repo URL to avoid the error:

```bash
!!! You are trying to log into this SSH server on port 22, which is not intended.

bandit27-git@localhost: Permission denied (publickey).
fatal: Could not read from remote repository.
```

Once cloned, you should see a directory named `repo`:

![image](https://github.com/user-attachments/assets/1209b78f-e7fc-4710-ac12-a26ba9cb33c8)

3. **Exploring the Repository*8
   
Navigate into the newly cloned `repo` directory. Take a closer look at its contents. Use the `ls -la` command to list all files, including hidden ones, with detailed permissions:

```bash
bandit27@bandit:/tmp/tmp.Ys3njYZfmY$ cd repo/
bandit27@bandit:/tmp/tmp.Ys3njYZfmY/repo$ ls -la
total 16
drwxr-sr-x 3 bandit27 root 4096 Jul  3 12:24 .
drwx--S--- 3 bandit27 root 4096 Jul  3 12:24 ..
drwxr-sr-x 8 bandit27 root 4096 Jul  3 12:24 .git
-rw-r--r-- 1 bandit27 root   68 Jul  3 12:24 README
```

Since there is only one `README` file in the repo, open it with the `cat` command to examine the contents:

![image](https://github.com/user-attachments/assets/4d059281-77fe-4d0e-aebc-1838e34986a5)

The `README` file holds the password for the next level.
