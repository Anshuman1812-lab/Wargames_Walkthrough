# OverTheWire Wargames: Bandit Level 22 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-64e05d60d9cd***

![image](https://github.com/user-attachments/assets/d70c0c6d-4991-415d-9d2d-40b51337dd87)

## Level Overview
***Bandit Level 22:** https://overthewire.org/wargames/bandit/bandit22.html*

***Goal:** The password for Level 22 is output by a program that is regularly executed via a cron job. To find it, examine the cron configuration in `/etc/cron.d` to understand what command is being run.*

***SSH:** ssh bandit21@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit21*

***Password:** EeoULMCra2q0dSkYj561DX7s1CpBuOBt*

![image](https://github.com/user-attachments/assets/33b535d8-0f4f-41ca-ae9f-24ab52e7f155)

## Solution
1. **Navigate to `/etc/cron.d`:**
   
Start by navigating to the cron directory using `cd /etc/cron.d`, where scheduled cron jobs for all users are defined.

2. **List and Identify Relevant Files:**
   
Use `ls -la` to view the contents and permissions of each file in `/etc/cron.d`:

![image](https://github.com/user-attachments/assets/62bfce35-e1ca-44b4-b8de-d78a65a212ed)

Among these files, `cronjob_bandit22` seems relevant because it’s likely configured to execute a command as `bandit22`.

3. **Examine the `cronjob_bandit22` File:**
   
Use `cat` to read the contents of `cronjob_bandit22`:

```bash
bandit21@bandit:/etc/cron.d$ cat cronjob_bandit22 
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
bandit21@bandit:/etc/cron.d$
```

This cron job executes the script `/usr/bin/cronjob_bandit22.sh` as the `bandit22` user every minute (`* * * * *`) and at system reboot (`@reboot`). The output is redirected to `/dev/null`, meaning it won’t appear in any logs, making it less obvious what the job is doing.

4. **Inspect the Script `/usr/bin/cronjob_bandit22.sh`:**
   
Next, examine the script that the cron job is executing:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

![image](https://github.com/user-attachments/assets/7464fb9c-e6d4-4313-8ecc-95185f11f023)

This script performs two actions:

- It sets the permissions of `/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv` to `644`, making the file readable by everyone (indicated by the last 4).
- It outputs the contents of `/etc/bandit_pass/bandit22` (the password file for Level 22) into this temporary file.

5. **Read the Password from the Temporary File:**
   
Since the file in `/tmp` is accessible, use `cat` to read the contents:

```bash
cat/tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```
![image](https://github.com/user-attachments/assets/85d2c3de-f032-417d-8bf9-865539aacc38)

This output is the password for Level 22.
