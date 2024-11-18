# Bandit Level 7 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-83d8d3bec83c***

![image](https://github.com/user-attachments/assets/18461d10-e052-48a0-9067-09709f5beadb)

## Level Overview
***Bandit Level 7:** https://overthewire.org/wargames/bandit/bandit7.html*

***Goal:** Find the password for Level 7, which is stored in a file that is:*

- *owned by the user `bandit7`.*
- *owned by the group `bandit6`.*
- *exactly 33 bytes in size.*

***SSH:** ssh bandit6@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit6*

***Password:** HWasnPhtq9AVKe0dmk45nxy20cvUa6EG*

![image](https://github.com/user-attachments/assets/f3dd98d0-aea8-4942-a3ac-1972d85d84c1)

## Solution
1. **Using `find` to Search with Multiple Filters:**
   
Since the file is somewhere on the server, start from the root directory (`/`):

![image](https://github.com/user-attachments/assets/c0c27677-4e08-47ab-b01e-bfc1fe3cbaab)

Use `find` with options to filter by owner, group, and file size. The command below will:

- Search recursively from the root.
- Look for files owned by `bandit7` (`-user bandit7`).
- Ensure files are owned by the group `bandit6` (`-group bandit6`).
- Restrict results to files exactly 33 bytes (`-size 33c`):
```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```
The `2>/dev/null` portion suppresses permission errors by redirecting them, making the output easier to read.

![image](https://github.com/user-attachments/assets/1957a16a-adcb-4889-aeed-2da141856636)

This command should return a single file path matching the criteria. Take note of this file path for the next step.

2. **Read the File to Get the Password:**

Use `cat` with the file path to display the file’s contents and retrieve the password:

```bash
cat /var/lib/dpkg/info/bandit7.password
```
![image](https://github.com/user-attachments/assets/a71a4c99-94e7-43e4-9e04-8e83267ae3c2)
