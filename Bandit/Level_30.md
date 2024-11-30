# OverTheWire Wargames: Bandit Level 30 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-58284e569a80***

![image](https://github.com/user-attachments/assets/ba03b407-a4d2-4ad5-890f-bceee0ab34cd)

## Level Overview
***Bandit Level 30:** https://overthewire.org/wargames/bandit/bandit30.html*

***Goal:** There is a git repository at `ssh://bandit29-git@localhost/home/bandit29-git/repo` via the port `2220`. The password for the user `bandit29-git` is the same as for the user `bandit29`.*
*Clone the repository and find the password for the next level.*

***SSH:** ssh bandit29@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit29*

***Password:** 4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7*

![image](https://github.com/user-attachments/assets/f7e12e15-f222-4fef-ab13-2c0921301668)

# Solution
1. **Clone the Repository**
   
As in previous levels, start by creating a temporary directory and cloning the repository. Then navigate to it and analyze the contents.

![image](https://github.com/user-attachments/assets/b8b97bc1-5e40-4f3f-b9a2-523e003bc52a)

2. **Check README.md Contents**
   
Inspect the `README.md` file:

![image](https://github.com/user-attachments/assets/89fa7910-e538-448e-aadc-8373db445496)

The `README.md` explicitly states that there are no passwords in production, hinting that we should look elsewhere.

3. **Explore the Repository’s Branches**
   
List all branches, both local and remote:

```bash
git branch -a
```

![image](https://github.com/user-attachments/assets/6ca045a9-1fc7-4697-8773-a60f1597dcfc)

This reveals two interesting remote branches: `dev` and `sploits-dev`. The dev branch looks promising since it’s often used for active development, where passwords might still be present.

4. **Switch to the Development Branch**
   
Switch to the `dev` branch and list out all the contents:

![image](https://github.com/user-attachments/assets/5159fa57-c692-40a6-844a-fbcde372f1a5)

5. **Inspect the `README.md` File**
   
Open the README.md file on the dev branch:

![image](https://github.com/user-attachments/assets/d1783638-08df-433f-a8da-dc7b6f370bca)

This version of the file contains the username and password.
