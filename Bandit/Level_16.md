# Bandit Level 16 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-da560bb14b68***

![image](https://github.com/user-attachments/assets/7b7f3bb8-4038-460c-a3bf-bd14c358da0e)

## Level Overview
***Bandit Level 16:** https://overthewire.org/wargames/bandit/bandit16.html*

***Goal:** Retrieve the password for Level 16 by submitting the current password to port `30001` on `localhost`, using SSL/TLS encryption.*

***SSH:** ssh bandit15@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit15*

***Password:** 8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo*

![image](https://github.com/user-attachments/assets/8682676e-2016-4fd4-9abf-02328d78bd62)

## Solution
1. **Confirm the Current Password:**
   
Ensure you have the password from Level 15. If you need to retrieve it, review the solution for the previous level.

![image](https://github.com/user-attachments/assets/09a56254-2cce-45f2-a668-588fd95bc1ec)

2. **Connect to Port 30001 Using SSL/TLS:**
   
Use `openssl s_client` to establish a secure connection to localhost on port 30001:

```bash
openssl s_client -connect localhost:30001
```

Here’s how this command works:

- `openssl s_client` initiates an SSL/TLS connection.
- `-connect localhost:30001` specifies the target address and port.

3. **Send the Password:**
   
Once connected, type the Level 15 password and press Enter to send it. The server should process your input and respond with the password for the next level.

```bash
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
.....
8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo
Correct!
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

closed
bandit15@bandit:~$
```

The server’s response should include the password for Level 16. Note it down.
