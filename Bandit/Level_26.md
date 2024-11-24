# OverTheWire Wargames: Bandit Level 26 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-b1f2c4b36c66***

![image](https://github.com/user-attachments/assets/518b0401-a05a-46f9-95e8-08f2fa20044a)

## Level Overview
***Bandit Level 26:** https://overthewire.org/wargames/bandit/bandit26.html*

***Goal:** Access the account for `bandit26`, which is configured to use a restricted shell. Determine the shell being used, understand its restrictions, and bypass them to gain a functional shell.*

***SSH:** ssh bandit25@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit25*

***Password:** iCi86ttT4KSNe1armKiwbQNmB3YJP3q4*

![image](https://github.com/user-attachments/assets/7ef37d18-4fa9-42e7-a806-ef6428aebaa6)

## Solution
1. **Determine the shell**
   
Each user has a user default shell. This is especially important when using `ssh`, because this is the shell that will be displayed. The information, what shell is the default for a user, can be found at the end of the line for the user in the `/etc/passwd` file.

First, determine the shell used by the `bandit26` by inspecting `/etc/passwd` from the `bandit25` account.

```bash
bandit25@bandit:~$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
bandit25@bandit:~$
```

The output indicates the shell used is `/usr/bin/showtext`, a custom script or program.

2. **Examine the `showtext` Script:**
   
From the `bandit25` account, inspect the `showtext` script and its permissions using `ls -la /usr/bin/showtext`.

![image](https://github.com/user-attachments/assets/b3d48b90-8c33-49bd-b069-6e7b27866ed3)

The script is executable by all users.

3. **Understand the Function of showtext:**
   
Use `cat /usr/bin/showtext` to analyze and understand its behavior.

![image](https://github.com/user-attachments/assets/374f00cc-833e-4ede-be26-ada121a56f25)

This script sets the `TERM` environment variable to `linux` and runs the `more` command to display the file `~/text.txt`. The exec replaces the current process with `more`, and the `exit 0` ensures a clean exit after `more` finishes.

4. **Log in to `bandit26`:**
   
Check the home directory of the current user for any SSH private key and use it to log into `bandit26`.

```bash
bandit25@bandit:~$ ssh -i bandit26.sshkey bandit26@localhost -p 2220
                         _                     _ _ _   
                        | |__   __ _ _ __   __| (_) |_ 
                        | '_ \ / _` | '_ \ / _` | | __|
                        | |_) | (_| | | | | (_| | | |_ 
                        |_.__/ \__,_|_| |_|\__,_|_|\__|

                      This is an OverTheWire game server. 

.
.
.

  Enjoy your stay!

  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/ 
Connection to localhost closed.
bandit25@bandit:~$
```

What’s happening here is that `/usr/bin/showtext` is executed which terminates the connection to `bandit26`.

Remember that the `more` command displays the very short text contained in the file `~/text.txt` which is:

```bash
  _                     _ _ _   ___   __  
 | |                   | (_) | |__ \ / /  
 | |__   __ _ _ __   __| |_| |_   ) / /_  
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \ 
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
```

This causes the entire text to be displayed immediately. After that, `exit 0` terminates the connection.

The purpose of the `more` command is to display the text that remains outside the terminal window. Making the terminal window smaller than the contents of the file `~/text.txt` makes the `more` command to go in the command/interactive mode.

Make the terminal window smaller and try to log intobandit26again.

![image](https://github.com/user-attachments/assets/8a5bea19-62ea-4e01-a9ad-309d23007d3c)

Once you see `--More--(83%)`, you can use `v` to enter the Vim editor as `bandit26` and rescale the window back to normal.

![image](https://github.com/user-attachments/assets/90f6bd64-5df3-4fb8-9bb0-90bc9a29c145)

5. **Bypass the Restricted Shell:**
   
Use the interactive features of the `more` command to escape into a functional shell. In `vi`, enter command mode by pressing `:` and change the default user shell from `/usr/bin/showtext` to `/bin/bash`:

```bash
  _                     _ _ _   ___   __
 | |                   | (_) | |__ \ / /
 | |__   __ _ _ __   __| |_| |_   ) / /_
 | '_ \ / _` | '_ \ / _` | | __| / / '_ \
 | |_) | (_| | | | | (_| | | |_ / /| (_) |
 |_.__/ \__,_|_| |_|\__,_|_|\__|____\___/
~                                        
~                                         
~                                         
~                                         
:set shell=/bin/bash                                 3,1           All
```

Confirm that the user default shell has changed to `/bin/bash` by using the command `:set shell?` You should get the output:

![image](https://github.com/user-attachments/assets/f6892249-a938-4bb0-b9ca-c28e93614459)

6. **Retrieve the Password:**
   
Finally, use `:shell` command to read the password for `bandit26`:

```bash
cat /etc/bandit_pass/bandit26
```

![image](https://github.com/user-attachments/assets/d7e1617e-c572-4fe5-81aa-b05cae08e54a)
