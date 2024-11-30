# OverTheWire Wargames: Bandit Level 31 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-55b79fa43a41***

![image](https://github.com/user-attachments/assets/6de0008a-3a9c-4391-b7fd-a51d2b282f6d)

## Level Overview
***Bandit Level 31:** https://overthewire.org/wargames/bandit/bandit31.html*

***Goal:** There is a git repository at `ssh://bandit30-git@localhost/home/bandit30-git/repo` via the port `2220`. The password for the user `bandit30-git` is the same as for the user `bandit30`.*
*Clone the repository and find the password for the next level.*

***SSH:** ssh bandit30@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit30*

***Password:** qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL*

![image](https://github.com/user-attachments/assets/4cd28a4b-9252-483f-b728-31bb5904127d)

## Solution
1. **Clone the Repository**
   
As always, start by creating a temporary directory and cloning the repository. Then, move into the cloned repository and analyze the contents.

![image](https://github.com/user-attachments/assets/8bfd1dbb-ba20-41a2-a7e4-e84dfbf0c5aa)

2. **Check `README.md` Contents**
   
The only visible file is `README.md`. Open it to check its contents:

![image](https://github.com/user-attachments/assets/ce765b30-4dee-4d5f-b826-eb6c24306cff)

The `README.md` file doesn’t provide any useful information. Time to dig deeper.

3. **Look for a way in**
   
I tried playing around with git commands to find something valuable. After exploring the logs and branches, something interesting finally showed up.

![image](https://github.com/user-attachments/assets/1c6a585a-eaaa-4e72-a8ce-199129cfc032)

The repository contains a single tag named `secret`. This looks promising!

4. **Inspect the Tag**
   
Use `git show` to display the details of the `secret` tag:

![image](https://github.com/user-attachments/assets/a27ae2ea-6bb1-4e5e-8b21-2f532efbe216)

The tag reveals the password for the next level.
