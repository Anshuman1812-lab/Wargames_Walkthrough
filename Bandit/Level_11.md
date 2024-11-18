# Bandit Level 11 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-36cf1e17ffa0***

![image](https://github.com/user-attachments/assets/8415ec2b-1395-466b-badd-f671bd43f144)

## Level Overview
***Bandit Level 11:** https://overthewire.org/wargames/bandit/bandit11.html*

***Goal:** The password for Level 11 is stored in `data.txt`, which contains data encoded in **base64** format. Your task is to decode this data to find the password.*

***SSH:** ssh bandit10@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit10*

***Password:** FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey*

![image](https://github.com/user-attachments/assets/a4836052-6116-45b2-a14e-11619156212d)

## Solution
1. **Locate and Inspect `data.txt`:**
   
Start by confirming that you’re in the directory containing `data.txt`.

![image](https://github.com/user-attachments/assets/911f4221-4ddd-4f6c-a124-9fa5da3c7158)

2. **Decode the Base64 Data:**
   
Use the `base64` command with the `-d` option to decode the contents of `data.txt` and output the decoded text:

```bash
base64 -d data.txt
```

`base64 -d` reads `data.txt` and decodes the base64-encoded content, displaying the decoded password.

![image](https://github.com/user-attachments/assets/f07e69ca-49a3-4af0-ae01-0838b72c9d35)

The decoded output will reveal the password for Level 11. Take note of this password.

