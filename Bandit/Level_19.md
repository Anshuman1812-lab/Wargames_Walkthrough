# OverTheWire Wargames: Bandit Level 19 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-cfa8270f3a72***

![image](https://github.com/user-attachments/assets/ff8e3325-dd82-427c-86c4-09027ff3c5c5)

## Level Overview
***Bandit Level 19:** https://overthewire.org/wargames/bandit/bandit19.html*

***Goal:** Retrieve the password for Level 19 from a file named `readme` in the home directory. However, logging in with SSH triggers a logout due to modifications in the `.bashrc` file.*

***SSH:** ssh bandit18@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit18*

***Password:** x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO*

![image](https://github.com/user-attachments/assets/a466b550-fd7e-4d7b-b642-233f673d4be0)

## Solution
1. **Bypass the Interactive Shell with Remote Command Execution:**
   
Instead of logging in interactively, use SSH to execute a single command that reads the readme file directly:

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 ls
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

Here’s how the command works:

- `ssh bandit18@bandit.labs.overthewire.org -p 2220` connects to the Bandit server as usual.
- `ls` or `cat readme` is executed remotely, bypassing the `.bashrc` logout trigger.

![image](https://github.com/user-attachments/assets/cde698e0-23c3-43f8-b9f4-e33c78b2ea92)

The output from this SSH command should display the contents of the `readme` file directly in your terminal, revealing the password for Level 19.

2. **Alternative solution**
   
Alternatively, you could use the same method of executing a command with SSH but use `/bin/bash` as a command to spawn a bash shell or use the `-t` flag, which allows a ‘pseudo-terminal’ to run on the target machine, this way we can run `/bin/sh`. This is especially useful if we have to do multiple commands because we do not need to repeat the SSH statement and password.

![image](https://github.com/user-attachments/assets/e774d6ed-8f5b-432c-9c51-0fc9fed571ef)

![image](https://github.com/user-attachments/assets/4676ff55-8f95-45b6-b60a-4918952fced2)
