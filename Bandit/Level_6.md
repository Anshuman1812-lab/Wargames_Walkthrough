# Bandit Level 6 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-72da98eb6e9d***

![image](https://github.com/user-attachments/assets/a8178ea6-c6b2-41da-84df-4961e0c72639)

## Level Overview
***Bandit Level 6:** https://overthewire.org/wargames/bandit/bandit6.html*

***Goal:** Find the password for Level 6, which is stored in a file located somewhere within the inhere directory. This file has three characteristics:*

- *It is human-readable.*
- *It is exactly 1033 bytes in size.*
- *It is not executable.*

***SSH:** ssh bandit5@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit5*

***Password:** 4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw*

![image](https://github.com/user-attachments/assets/58f8f656-c10c-4384-b5a4-440ebb7c85d4)

## Solution
1. **Navigate to the `inhere` Directory:**
   
Start by moving to the `inhere` directory:

![image](https://github.com/user-attachments/assets/3ba2e769-6c28-466f-9467-4742f7e89567)

2. **Locate the required file:**
   
To locate the file with the required properties in the entire directory, use `find` with options to specify:

- Size (`-size 1033c` for files of exactly 1033 bytes).
- Human-readability (`file` command will verify this).
- Non-executability (`! -executable`).

Run the following command:

```bash
find . -type f -size 1033c ! -executable
```
![image](https://github.com/user-attachments/assets/855333d1-b91c-4138-a400-7f07f49f7303)

This command searches recursively (`.` specifies the current directory) for regular files (`-type f`) that match the size (`-size 1033c`), are not executable (`! -executable`), and returns the filename(s).

3. **Confirm the File is Human-Readable:**
   
Use the `file` command on the located file to verify it is human-readable by running:

```bash
file maybehere07/.file2
```
![image](https://github.com/user-attachments/assets/164b5635-213a-4a06-8643-d5e210d1b091)

4. **Read the File to Obtain the Password:**
   
Use `cat` to display the file’s contents and retrieve the password:
![image](https://github.com/user-attachments/assets/f3940edb-2421-4605-bf19-e25eba64439f)
