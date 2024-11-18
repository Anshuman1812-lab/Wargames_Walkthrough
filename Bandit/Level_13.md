# Bandit Level 13 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-aefcb7058760***

![image](https://github.com/user-attachments/assets/a082d851-3896-429c-9468-be235aa09f49)

## Level Overview
***Bandit Level 13:** https://overthewire.org/wargames/bandit/bandit13.html*

***Goal:** The password for Level 13 is stored in `data.txt`, which is a hexdump of a file that has undergone multiple rounds of compression. You’ll need to decode the hexdump and repeatedly decompress it until you reveal the password.*

***SSH:** ssh bandit12@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit12*

***Password:** 7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4*

![image](https://github.com/user-attachments/assets/18178bdb-6e44-4341-ac0a-a4f54a4ddc97)

## Solution
1. **Create a Temporary Working Directory:**
   
Since you’ll be handling multiple files, it’s best to work in a dedicated temporary directory. Use mktemp to create a uniquely named directory under `/tmp`:

```bash
cd /tmp
mktemp -d
```
![image](https://github.com/user-attachments/assets/79e2ed72-2575-4c37-91e7-3c15babef5e4)

2. **Copy `data.txt` to the Working Directory:**

Copy `data.txt` from the original location to your temporary working directory and confirm the file format:

![image](https://github.com/user-attachments/assets/3e82ba8e-d43d-4054-8a65-9331720c1be5)

3. **Convert Hexdump to Binary:**

Use `xxd` to convert `data.txt` from hexdump back into a binary file:

```bash
xxd -r data.txt data.bin
```

Here, `-r` reverses the hexdump to its original binary format.

![image](https://github.com/user-attachments/assets/4ce59438-76a0-4880-9c89-fff03b1b9431)

4. **Identify Compression Type and Decompress:**
   
Use the `file` command to check the format of `data.bin` to identify the type of compression. For example:

![image](https://github.com/user-attachments/assets/99b03608-dd48-4216-a971-da29051b78f5)

Based on the output, apply the corresponding decompression tool:

- For gzip: `mv data.bin data.gz && gzip -d data.gz`
- For bzip2: `mv data.bin data.bz2 && bzip2 -d data.bz2`
- For tar: `tar -xf data.bin`
  
5. **Repeat Decompression:**
   
After each decompression, use `file` again to determine the next format. Continue the cycle of identifying and decompressing until you reach a readable text file.

![image](https://github.com/user-attachments/assets/c4b5065b-c3a3-4411-8969-66896dac9f7d)

6. **Read the Password:**
   
Once you reach the final, human-readable file, use `cat` to view its contents and reveal the password:

![image](https://github.com/user-attachments/assets/594e4795-3726-4186-8ce5-6c2ae9f7bcf2)
