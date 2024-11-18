# Bandit Level 15 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-2c83c228cd88***

![image](https://github.com/user-attachments/assets/7d168bd3-6049-4ce1-b996-b609fc15baa9)

## Level Overview
***Bandit Level 15:** https://overthewire.org/wargames/bandit/bandit15.html*

***Goal:** Send the password for Level 14 to port `30000` on `localhost` to receive the password for Level 15 in response.*

***SSH:** ssh bandit14@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit14*

***Password:** MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS*

![image](https://github.com/user-attachments/assets/e3789089-47cb-4824-a0c8-89b1f8a181ce)

## Solution
1. **Confirm the Current Password:**
   
Ensure you have the current password from Level 14. If needed, review the previous level’s solution to retrieve it.

![image](https://github.com/user-attachments/assets/fb2477de-9eae-4c46-ac76-1dcfbe1b4906)

2. **Connect to Port `30000` on `localhost`:**

Use `nc` (Netcat) to connect to `localhost` on port `30000`. This command establishes a connection to the specified port:

```bash
nc localhost 30000
```

After connecting, type the password for Level 14 and press Enter to send it through the connection.

![image](https://github.com/user-attachments/assets/0ecc98e8-f570-4647-88c3-2ab390aad746)

3. **Send the Password:**
   
Alternatively, you can also use input redirection to send the password directly:

```bash
echo "MU4VWeTyJk8R0of1qqmcBPaLh7lDCPvS" | nc localhost 30000
```
![image](https://github.com/user-attachments/assets/0eae38ac-24d1-4157-b207-445187b67434)

The output should display the password for Level 15. Note this password for use in the next level.

