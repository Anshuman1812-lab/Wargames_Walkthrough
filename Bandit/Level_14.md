# Bandit Level 14 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-0194c3722603***

![image](https://github.com/user-attachments/assets/81b11b1e-bcf9-411f-8c91-bc7d84b84574)

## Level Overview
***Bandit Level 14:** https://overthewire.org/wargames/bandit/bandit14.html*

***Goal:** Access the password for Level 14, stored in `/etc/bandit_pass/bandit14`, which is only readable by the bandit14 user. Instead of a password, you’ll use a private SSH key provided for this level to log in as `bandit14`.*

***SSH:** ssh bandit13@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit13*

***Password:** FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn*

![image](https://github.com/user-attachments/assets/361e1122-8f26-460f-9aa7-2c491eaa506e)

## Solution
1. **Locate the Private SSH Key:**
   
Use `ls` to check the home directory and identify the SSH key file, likely named something like `sshkey.private`:

![image](https://github.com/user-attachments/assets/2ba224c6-fa4d-44c5-9b83-478d6bf21483)

2. **Connect to `bandit14` Using the SSH Key:**
   
Use the `ssh` command to connect as bandit14 via `localhost`, specifying the key file with `-i`:

```bash
ssh -i sshkey.private bandit14@localhost -p 2220
```

Here’s how each part of the command works:

- `-i sshkey.private` tells SSH to use the specified identity file (here, private key) for authentication.
- `bandit14@localhost` specifies the user and server (localhost refers to the current machine).
- `-p 2220` specifies the non-standard port for the SSH connection.

![image](https://github.com/user-attachments/assets/fee3dcb3-bfb0-43ef-b5ef-cf807538bda9)

3. **Retrieve the Password:**
   
Once logged in as `bandit14`, use cat to read the password from `/etc/bandit_pass/bandit14`:

```bash
cat /etc/bandit_pass/bandit14
```

The output will display the password for Level 14.

![image](https://github.com/user-attachments/assets/36ce4d13-b190-4403-8ae8-96247090d753)
