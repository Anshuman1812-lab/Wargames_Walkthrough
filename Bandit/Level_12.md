# Bandit Level 12 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-25fe60157a26***

![image](https://github.com/user-attachments/assets/2723991c-4d23-4278-a881-f3f49dd10374)

## Level Overview
***Bandit Level 12:** https://overthewire.org/wargames/bandit/bandit12.html*

***Goal:** Find the password for Level 12 in `data.txt`, where all letters have been shifted by 13 positions using ROT13 encoding.*

***SSH:** ssh bandit11@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit11*

***Password:** dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr*

![image](https://github.com/user-attachments/assets/f212b7e6-e00d-4516-82bf-0dc21edae41e)

## Solution
1. **Locate and Inspect `data.txt`:**
   
Start by confirming that you’re in the directory containing `data.txt`.

![image](https://github.com/user-attachments/assets/03ad0449-2284-4972-b0c9-25232af01d21)

2. **Decode the ROT13-Encoded Text:**
   
Use the `tr` command to apply ROT13 to the file’s contents. ROT13 can be done with `tr` by mapping `a-zA-Z to n-za-mN-ZA-M`:

```bash
cat data.txt | tr 'a-zA-Z' 'n-za-mN-ZA-M'
```

Here’s how the command works:

- `cat data.txt` reads the contents of `data.txt`.
- `|` (pipe) sends the output to `tr`.
- `tr 'a-zA-Z' 'n-za-mN-ZA-M'` translates each letter in the file 13 positions forward (or backward) in the alphabet, effectively decoding the ROT13 text.

![image](https://github.com/user-attachments/assets/2cfd33a5-3167-4928-8ecf-3f8e30f199d3)

The output of this command will display the decoded text, which includes the password for Level 12. Note this password for the next step.
