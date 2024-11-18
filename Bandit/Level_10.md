# Bandit Level 10 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-3a4e8bd983df***

![image](https://github.com/user-attachments/assets/161cc49c-3430-4221-bcf4-3df192a42b5f)

## Level Overview
***Bandit Level 10:** https://overthewire.org/wargames/bandit/bandit10.html*

***Goal:** Find the password for Level 10, which is embedded in `data.txt` as one of the few human-readable strings. This string is recognizable because it’s preceded by several `=` characters.*

***SSH:** ssh bandit9@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit9*

***Password:** 4CKMh1JI91bUIZZPXDqGanal4xvAg0JM*

![image](https://github.com/user-attachments/assets/4757bcb3-d7a7-48b0-8c6e-9867c6d4725c)

## Solution
1. **Locate and Inspect `data.txt`:**
   
Ensure you’re in the directory containing `data.txt`.

![image](https://github.com/user-attachments/assets/aca90c9e-f556-4478-be0e-a7677551366b)

![image](https://github.com/user-attachments/assets/45f48bd4-b7c4-44a4-b6a8-ee57f26c7882)

2. **Extract Human-Readable Text:**
   
The `strings` command scans binary files and outputs only human-readable text. Use it to filter readable strings in `data.txt`:

```bash
strings data.txt
```
![image](https://github.com/user-attachments/assets/f10c0da7-5f51-43c8-b2e5-6bb08e1db8a7)

3. **Search for the Target Pattern:**
   
Since the password is preceded by multiple `=` characters, pipe the output of `strings` to `grep` and look for lines containing `=`:

```bash
strings data.txt | grep "==="
```

`grep "==="` searches for strings with three or more `=` characters, which likely precede the password.

![image](https://github.com/user-attachments/assets/d74d9c9d-a485-4ae9-9c41-6d7e0c081da7)

The output should include the line with the `=` characters and the password. Take note of this password.
