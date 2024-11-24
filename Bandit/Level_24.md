# OverTheWire Wargames: Bandit Level 24 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-450299eb9b2e***

![image](https://github.com/user-attachments/assets/59a34457-3909-4b44-9b14-f4b5df4b2ed9)

## Level Overview
***Bandit Level 24:** https://overthewire.org/wargames/bandit/bandit24.html*

***Goal:** The password for the next level can be accessed by creating a shell script that the cron job will execute. The script must be placed in a specific directory so it can be run automatically by the `bandit24` user’s cron job.*

***SSH:** ssh bandit23@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit23*

***Password:** 0Zf11ioIjMVN551jX3CmStKLYqjk54Ga*

![image](https://github.com/user-attachments/assets/3a47fa05-9bf9-47ce-b63a-1dbc467d630f)

## Solution
1. **Navigate to `/etc/cron.d`:**
   
Begin by navigating to the directory using `cd /etc/cron.d`, where scheduled cron jobs for all users are defined.

2. **List and Examine Cron Files:**
   
Use `ls -la` to view the contents and permissions of each file in `/etc/cron.d`:

![image](https://github.com/user-attachments/assets/1e88e79c-c8e2-47e9-bbda-83670a068c09)

Among these files, `cronjob_bandit24` seems relevant because it’s likely configured to execute a command as `bandit24`.

3. **Inspect `cronjob_bandit24`:**
   
Use `cat` to display the contents of `cronjob_bandit24`, which shows the schedule and command executed by the cron job:

![image](https://github.com/user-attachments/assets/f22ae56e-0eec-46d6-aa10-fab99d23d5c6)

This cron job runs `cronjob_bandit24.sh` every minute (`* * * * *`) and at system reboot. The output is redirected to `/dev/null`, so we need to explore the script itself.

4. **Examine `/usr/bin/cronjob_bandit24.sh`:**
   
Use `cat` to read the `/usr/bin/cronjob_bandit24.sh`, which contains the commands executed by the cron job:

![image](https://github.com/user-attachments/assets/6fad7ebb-dbb5-4307-9706-569a2bb906e3)

This script does the following:

- Changes the directory to `/var/spool/bandit24/foo`.
- Iterates through all files in this directory.
- If a file is owned by `bandit23`, the script executes it with a 60-second timeout, then deletes it.

5. **Create your own script in `/var/spool/bandit24/foo`:**
   
Write a script that outputs the password for `bandit24` and save it in `/var/spool/bandit24/foo`. Use the following steps:

- Create the script in your home directory for safekeeping:

```bash
echo 'cat /etc/bandit_pass/bandit24 > /tmp/bandit24_password' > /tmp/myscript.sh
```

- Make the script executable:

```bash
chmod +x /tmp/myscript.sh
```

- Move the script to `/var/spool/bandit24/foo`:

```bash
mv /tmp/myscript.sh /var/spool/bandit24/foo
```

![image](https://github.com/user-attachments/assets/83236b78-d8e9-497d-9dcc-c985cb6e8f8d)

6. **Wait for the Cron Job to Execute:**

The cron job runs every minute, so after 60 seconds, it should execute `myscript.sh`. This script will save the bandit24 password in `/tmp/bandit24_password`.

7. **Read the Password from the Temporary File:**
   
Once the script has been executed, `cat` to read the password from `/tmp/bandit24_password`:

![image](https://github.com/user-attachments/assets/aa3bedc3-50a7-4c79-b69a-836be4b785b6)

The output is the password for Level 24.
