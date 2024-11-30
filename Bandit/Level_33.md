# OverTheWire Wargames: Bandit Level 33 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-92647119ac96***

![image](https://github.com/user-attachments/assets/caeb6062-c509-4000-ab3e-1af5b3a1f9ef)

## Level Overview
***Bandit Level 33:** https://overthewire.org/wargames/bandit/bandit33.html*

***Goal:** After all this `git` stuff, it’s time for another escape. Good luck!*

***SSH:** ssh bandit32@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit32*

***Password:** 3O9RfhqyAlVBEZpVb6LYStshZoqoSx5K*

![image](https://github.com/user-attachments/assets/861b5d95-257d-4612-b903-b458acbfbf80)

## Solution
When you log in using SSH, you’re greeted with an unusual prompt:

![image](https://github.com/user-attachments/assets/38548fa8-d2b9-4d29-9bd5-1e547a432ce5)

It’s immediately clear that something unconventional is at play. Let’s dive into how to tackle this unique shell.

1. **Understanding the `UPPERCASE SHELL`**
   
Testing the waters with basic commands quickly reveals an unusual limitation.

![image](https://github.com/user-attachments/assets/867ba3a2-1584-4ead-9e7b-d3031f387ac4)

It appears the shell converts all your input to uppercase, rendering typical lowercase commands ineffective. Given that most Linux commands are case-sensitive and written in lowercase, this presents a peculiar challenge. We need a creative way to bypass the forced uppercase conversion.

2. **Exploiting Variables for Escape**
   
Linux environment variables come to the rescue. Variables are a staple of Linux, and they are case-sensitive — many of them use uppercase by convention. Among these, the `$0` variable holds a reference to the current shell. This key insight lets us execute the default shell directly, bypassing the restrictive environment.

![image](https://github.com/user-attachments/assets/c1c8657a-22e3-43d9-9215-15342077cbc6)

Executing `$0` drops you into a standard shell environment where commands work as expected.

3. **Inspecting the Environment**
   
Once free from the uppercase shell, the next logical step is to inspect your surroundings. The file `uppershell` is intriguing. It’s owned by `bandit33` and has the SUID (Set User ID) bit set. This means that when executed, it runs with the permissions of the file’s owner (`bandit33`), regardless of the user who executes it. This clue strongly suggests that you’re operating with elevated privileges, specifically as the `bandit33` user.

4. **Retrieving the Final Password**
   
After confirming the identity, armed with `bandit33` privileges, you now have access to the password file for this level. Retrieve it with:

![image](https://github.com/user-attachments/assets/746c7f90-5a1c-4171-8a70-329f498af6d8)

This reveals the final password.

5. **Final Verification**
   
To ensure everything is in order, log in one last time using the retrieved password.

***SSH:** ssh bandit33@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit33*

***Password:** tQdtbs5D5i2vJwkO8mEyYEyTL8izoeJ0*

![image](https://github.com/user-attachments/assets/d92cf8ec-d1b8-441e-b9a3-514bad174481)

6. **Check `README.txt` contents**
   
Upon doing so, you’ll find a file named `README.txt`. Opening it reveals the congratulatory message:

![image](https://github.com/user-attachments/assets/7ecb4d03-1072-431f-b080-19250f1aa775)
