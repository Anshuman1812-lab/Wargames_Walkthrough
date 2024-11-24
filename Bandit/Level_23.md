# OverTheWire Wargames: Bandit Level 23 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-326f9e01a814***

![image](https://github.com/user-attachments/assets/3739d88e-3f64-46ee-bebd-c8dd1b1a87f3)

## Level Overview
***Bandit Level 23:** https://overthewire.org/wargames/bandit/bandit23.html*

***Goal:** Identify the cron job for `bandit23`, examine the script it runs, and find the output that contains the password for Level 23.*

***SSH:** ssh bandit22@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit22*

***Password:** tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q*

![image](https://github.com/user-attachments/assets/a95cebc5-ab13-4dab-90bd-c6645f32bb26)

## Solution
1. **Navigate to `/etc/cron.d`:**
   
Begin by navigating to the directory using `cd /etc/cron.d`, where scheduled cron jobs for all users are defined.

2. **List and Examine Cron Files:**
   
Use `ls -la` to view the contents and permissions of each file in `/etc/cron.d`:

![image](https://github.com/user-attachments/assets/4dcfc60e-3084-458e-bb52-f3cadccbc40d)

Among these files, `cronjob_bandit23` seems relevant because it’s likely configured to execute a command as `bandit23`.

3. **Inspect `cronjob_bandit23`:**
   
Use `cat` to display the contents of `cronjob_bandit23`, which shows the schedule and command executed by the cron job:

![image](https://github.com/user-attachments/assets/ae43b0f2-d87a-4c16-9208-c9f6b3042f4e)

This cron job runs `cronjob_bandit23.sh` every minute (`* * * * *`) and at system reboot. The output is redirected to `/dev/null`, so we need to explore the script itself.

4. **Examine /usr/bin/cronjob_bandit23.sh:**
   
Use `cat` to read the `/usr/bin/cronjob_bandit23.sh`, which contains the commands executed by the cron job:

![image](https://github.com/user-attachments/assets/a402f1dc-af26-4560-ba0f-536dda5f608b)

Here’s what each part of the script does:

- `myname=$(whoami)`: Sets myname to the current username (`bandit23`).
- `mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)`: Creates an MD5 hash of the string "I am user bandit23" and stores it in `mytarget`.
- `cat /etc/bandit_pass/$myname > /tmp/$mytarget`: Copies the password file for `bandit23` into `/tmp`, using the hash as the filename.

5. **Generate the Hash Filename:**
   
To determine the exact filename in `/tmp`, replicate the hash generation by running:

```bash
bandit22@bandit:/etc/cron.d$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:/etc/cron.d$
```

This hash is the name of the file in `/tmp` that stores the password.

6. **Read the Password File:**
   
Use `cat` to read the file in `/tmp/8ca319486bfbbc3663ea0fbe81326349`:

![image](https://github.com/user-attachments/assets/1cfd8ba7-0125-41d3-a59b-046e6d09cef0)

The output is the password for Level 23.OverTheWire Wargames: Bandit Level 23 Walkthrough
