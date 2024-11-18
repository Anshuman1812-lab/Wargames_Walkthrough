# Bandit Level 17 Walkthrough_
***https://medium.com/@anshumansingh_71873/overthewire-wargames-1089730e54a4***

![image](https://github.com/user-attachments/assets/3a025a54-8451-4a49-8bc8-6d880b668ea0)

## Level Overview
***Bandit Level 17:** https://overthewire.org/wargames/bandit/bandit17.html*

***Goal:** The password for Level 17 can be obtained by sending the current level’s password to a server listening on one of the ports in the range 31000–32000. First, identify which ports have active servers, then determine which ones support SSL/TLS, and locate the correct server.*

***SSH:** ssh bandit16@bandit.labs.overthewire.org -p 2220*

***Server:** bandit.labs.overthewire.org*

***Port:** 2220*

***Username:** bandit16*

***Password:** kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx*

![image](https://github.com/user-attachments/assets/d17fe54d-9db8-4a04-8544-dee7cc7d7885)

## Solution
1. **Identify Open Ports with Nmap:**
   
To scan for open ports between 31000 and 32000, we can use `nmap` with service discovery enabled. This will check each port to see if it’s open and determine the service running on each of them.

```bash
nmap -p 31000-32000 -sV localhost
```

This command will perform a service version detection scan (`-s`V) across the specified port range (`-p 31000-32000`). This method combines the port scan and service discovery in one step, which can be faster than separating them.

![image](https://github.com/user-attachments/assets/7306583b-f852-4211-b4e8-32aa767a09f7)

2. **Analyze Nmap Results:**
   
Nmap will output a list of open ports and indicate whether each one supports SSL/TLS. It shows five open ports, with only two (`31518` and `31790`) supporting SSL.

Out of these two ports, port31518is running only an echo service, which suggests it won’t return useful credentials. However, port`31790`is running an unknown SSL service, which makes it a likely candidate.

3. **Connect to the SSL-Enabled Port Using OpenSSL:**
   
Using `openssl s_client`, connect to port `31790` on `localhost`. Once connected, enter the Level 16 password and press Enter to send it. If the port is correct, the server will respond with a private SSH key instead of echoing the password back.

```bash
bandit15@bandit:~$ openssl s_client -connect localhost:31790
...
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

4. **Save the Private SSH Key:**
   
Copy the key output and paste it into a new file (e.g.,`key.private`). Ensure the file has restricted permissions, as required for SSH key files:

```bash
chmod 600 key.private
```

With the private key saved and permissions set, use it to log into **bandit17** and retrieve the password:

```bash
ssh -i key.private bandit17@localhost -p 2220
```

![image](https://github.com/user-attachments/assets/68639004-7a6a-4e8b-b44f-80828476b145)
![image](https://github.com/user-attachments/assets/b075cb19-9f71-4957-bc23-9982d56d2f11)

