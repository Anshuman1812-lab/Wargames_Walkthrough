# Bandit Level 8 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-c010b1e764ca***

![image](https://github.com/user-attachments/assets/fa600ee7-cca6-40df-ae52-8e3b417af225)

## Level Overview
***Bandit Level 8:** https://overthewire.org/wargames/bandit/bandit8.html*

***Goal:** Locate the password for Level 8, which is stored in the file `data.txt` and appears next to the word **millionth**.*

***SSH:** ssh bandit7@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit7*

***Password:** morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj*

![image](https://github.com/user-attachments/assets/d1a8b009-5e06-4a84-bbcc-586deb2ff860)

## Solution
1. **Locate the `data.txt` File:**
   
Start by ensuring you’re in the correct directory where data.txt is located, which is usually the home directory (`~`). Confirm that `data.txt` is listed.

![image](https://github.com/user-attachments/assets/d408c8dd-b1e0-42c2-9c9b-fdcbb7da430c)

2. **Search for the Keyword with `grep`:**
   
Use `grep` to search within `data.txt` for lines containing the word **millionth**. This command will locate and display the line with the keyword:

```bash
grep "millionth" data.txt
```

Alternatively, you can use `cat` to display the contents of `data.txt` and filter the desired lines of the output using `grep`.

```bash
cat data.txt | grep "millionth"
```

`grep` searches each line for the specified word and returns the line that matches, displaying both “millionth” and the password next to it.

![image](https://github.com/user-attachments/assets/dc9d7a79-2a21-40d1-8121-7cbd6dc923f9)

The output from `grep` will display the line with **millionth** followed by the password. Note this password for the next level.
