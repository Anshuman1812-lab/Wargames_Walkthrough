# OverTheWire Wargames: Bandit Level 21 Walkthrough
***https://medium.com/@anshumansingh_71873/overthewire-wargames-adb867c716ed***

![image](https://github.com/user-attachments/assets/6368b612-dba7-4937-9924-70c4de148e0c)

## Level Overview
***Bandit Level 21:** https://overthewire.org/wargames/bandit/bandit21.html*

***Goal:** Use the setuid binary in the home directory to connect to a specified port on `localhost`. This binary will check the password for Level 20 against input received over the connection. If it matches, it will return the password for Level 21.*

***SSH:** ssh bandit20@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit20*

***Password:** 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO*

![image](https://github.com/user-attachments/assets/865f81da-5155-4e13-862a-f45dffa65cda)

## Solution
1. **Identify the Setuid Binary:**
   
Begin by listing files in the home directory to confirm the presence of the setuid binary:

![image](https://github.com/user-attachments/assets/3780467c-8578-4e56-8b02-1a8275a36311)

2. **Set Up a Network Listener with Netcat:**
   
Use `nc` (Netcat) to start a listening session on localhost on an available port (e.g., `12345`). This listener will wait to receive data from the setuid binary:

```bash
bandit20@bandit:~$ nc -lvp 12345
Listening on 0.0.0.0 12345
```

Here’s what each part of the command does:

- `-l` tells `nc` to listen for incoming connections.
- `-v` enables verbose output, useful for debugging.
- `-p 12345` specifies the port to listen on (choose any available port in the range).

3. **Run the Setuid Binary with the Port as an Argument:**
   
Open a second terminal or use job control to run the setuid binary with the listening port as its argument. This binary will attempt to connect to the specified port on `localhost` and send a request for authentication:

```bash
bandit20@bandit:~$ ./suconnect 12345
```

4. **Send the Password Over the Connection:**
   
In the `nc` session, input the password from Level 20 and press Enter. The setuid binary will check the password against what’s stored in `bandit20`.

```bash
bandit20@bandit:~$ nc -lvp 12345
Listening on 0.0.0.0 12345
Connection received on localhost 55034
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
```

If correct, will return the password for Level 21.

```bash
bandit20@bandit:~$ ./suconnect 12345
Read: 0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
Password matches, sending next password
```

5. **Retrieve the Password:**
   
The password for Level 21 will appear in the `nc` output if the password entered matches. Copy this password.

```bash
bandit20@bandit:~$ nc -lvp 12345
Listening on 0.0.0.0 12345
Connection received on localhost 55034
0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO
EeoULMCra2q0dSkYj561DX7s1CpBuOBt
bandit20@bandit:~$
```
