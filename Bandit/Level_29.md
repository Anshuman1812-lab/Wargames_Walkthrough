# OverTheWire Wargames: Bandit Level 29 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-01d4f068bdd5***

![image](https://github.com/user-attachments/assets/3061189c-283b-4586-b99d-815733e1e09a)

## Level Overview
***Bandit Level 29:** https://overthewire.org/wargames/bandit/bandit29.html*

***Goal:** There is a git repository at `ssh://bandit28-git@localhost/home/bandit28-git/repo` via the port `2220`. The password for the user `bandit28-git` is the same as for the user `bandit28`.*
*Clone the repository and find the password for the next level.*

***SSH:** ssh bandit28@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit28*

***Password:** Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN*

*![image](https://github.com/user-attachments/assets/92a0f28e-f5ad-4e41-9b8a-65b3b75e6cde)

## Solution
1. **Clone the Repository**
   
Just like the previous level, we begin by creating a temporary directory for our work and cloning the repository into it.

When prompted, enter the `bandit28` password to authenticate. After cloning, navigate into the `repo` directory and check the contents:

![image](https://github.com/user-attachments/assets/0a9eb8f8-0f66-444d-8022-0253fc765d91)

2. **Check `README.md` Contents**
   
There’s a `README.md` file that seems promising. Let’s open it:

![image](https://github.com/user-attachments/assets/948e4939-df24-4ae3-a0ae-18a5ba121c40)

While it lists the username and password field, the actual password has been redacted. Time to dig into the Git history to see if previous versions of the file reveal anything useful.

3. **Investigate the Git History**
   
Start by viewing the commit history with `git log`:

![image](https://github.com/user-attachments/assets/c3022aa4-aa80-4d97-ae89-32f229037a55)

Among the commit descriptions, `fix info leak` stands out. This might indicate a patch to hide sensitive information. Let’s inspect the changes made in that commit.

4. **Examine the Commit**
   
Use `git show` to see the content of the suspicious commit:

![image](https://github.com/user-attachments/assets/5529256f-6a52-42f6-b7cd-727c260095fc)

The output shows that the password field previously contained the plaintext value. This is the password we’ve been looking for!
