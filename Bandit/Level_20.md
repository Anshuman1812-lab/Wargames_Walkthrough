# OverTheWire Wargames: Bandit Level 20 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-19455a7c78d3***

![image](https://github.com/user-attachments/assets/988b2465-cf89-4519-8395-9199cefbf56a)

## Level Overview
***Bandit Level 20:** https://overthewire.org/wargames/bandit/bandit20.html*

***Goal:** To access the password for Level 20, use the setuid binary located in the home directory. This binary, when executed, temporarily grants elevated privileges, allowing you to read the password file stored in `/etc/bandit_pass/bandit20`.*

***SSH:** ssh bandit19@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit19*

***Password:** cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8*

![image](https://github.com/user-attachments/assets/60f65f50-d4cd-496a-a2b4-9adef072ecdd)

## Solution
1. **Locate the Setuid Binary:**
   
Begin by listing the contents of the home directory to identify the setuid binary:

![image](https://github.com/user-attachments/assets/8686902d-dbcd-4c22-8958-e37de11444d8)

In this case, the owner is `bandit20` and the group is `bandit19` , this file permission `-rwsr-x---` means the `bandit19` can execute the binary, but the binary is executed as `bandit20`.

2. **Execute the Binary to Understand Its Usage:**
   
Run the binary without any arguments to see if it displays usage instructions.

```bash
./bandit20-do
```

Often, the binary will provide guidance on its function or automatically display the password.

![image](https://github.com/user-attachments/assets/e26d0009-a317-4921-a2f8-6ff79dbc8aca)

3. **Use the Binary to Read the Password File:**
Since the setuid binary runs with elevated permissions, it can access `/etc/bandit_pass/bandit20`. Provide the path to the password file as an argument and execute the binary as follows to reveal the password:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```
![image](https://github.com/user-attachments/assets/37158112-d6bc-46c4-a83f-9ff7186899f4)

The binary should output the contents of the password file, displaying the password for Level 20.
