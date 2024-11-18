# Bandit Level 9 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-1d9d3a736db5***

![image](https://github.com/user-attachments/assets/5d5468fc-dac0-40b5-a261-a2dcec5d877c)

## Level Overview
***Bandit Level 9:** https://overthewire.org/wargames/bandit/bandit9.html*

***Goal:** Find the password for Level 9, which is stored in `data.txt` as the only line that appears only once in the file.*

***SSH:** ssh bandit8@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit8*

***Password:** dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc*

![image](https://github.com/user-attachments/assets/89df12bb-6c9e-43b6-9cbf-4d489b3978c4)

## Solution
1. **Locate the `data.txt` File:**
   
First, confirm that you’re in the directory containing `data.txt`.

![image](https://github.com/user-attachments/assets/573be860-af00-43e6-95d5-49252f1a5c93)

Verify that `data.txt` is listed in the output.

2. **Sort the File and Identify Unique Lines:**

![image](https://github.com/user-attachments/assets/6a695e63-0092-42b4-8e15-6cf6af9d7d59)

To find the unique line, use `sort` to organize the lines in `data.txt`.

![image](https://github.com/user-attachments/assets/d8aa4a6c-274f-443f-899d-84dde3c902b5)

Pipe the output of` sort` to `uniq` with the `-u` option to isolate lines that appear only once:

```bash
sort data.txt | uniq -u
```

Here’s what each part does:

- `sort` arranges the lines in alphabetical order, grouping identical lines together.
- `uniq -u` filters out duplicate lines, leaving only lines that occur once.

![image](https://github.com/user-attachments/assets/ba75a13a-f802-4994-9b7c-e906f83dee52)

The output should display the unique line, which contains the password for Level 9. Take note of this password for the next step.
