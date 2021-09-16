
```
┌──(xnv㉿kali)-[~]
└─$ nmap -A 10.10.49.240

Starting Nmap 7.80 ( https://nmap.org ) at 2020-06-16 04:08 EDT
Nmap scan report for lazyadmin.com (10.10.240.121)
Host is up (0.26s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 49:7c:f7:41:10:43:73:da:2c:e6:38:95:86:f8:e0:f0 (RSA)
|   256 2f:d7:c4:4c:e8:1b:5a:90:44:df:c0:63:8c:72:ae:55 (ECDSA)
|_  256 61:84:62:27:c6:c3:29:17:dd:27:45:9e:29:cb:90:5e (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 38.82 seconds
```

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.49.240/FUZZ -t 100

=====================================================================
ID           Response   Lines    Word       Chars       Payload
=====================================================================
000000001:   200        375 L    968 W      11321 Ch    "http://10.10.49.240/"
000001027:   301        9 L      28 W       314 Ch      "content"
000002020:   200        375 L    968 W      11321 Ch    "index.html"
```

```
teste2 
```

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.49.240/content/FUZZ -t 100
=====================================================================
ID           Response   Lines    Word       Chars       Payload 
=====================================================================
000000001:   200        35 L     151 W      2198 Ch     "http://10.10.49.240/content/"
000000478:   301        9 L      28 W       317 Ch      "as"
000000505:   301        9 L      28 W       325 Ch      "attachment"
000000089:   301        9 L      28 W       322 Ch      "_themes"
000001991:   301        9 L      28 W       321 Ch      "images"
000002010:   301        9 L      28 W       318 Ch      "inc"
000002021:   200        35 L     151 W      2198 Ch     "index.php"
000002179:   301        9 L      28 W       317 Ch      "js"
```

```
teste2 
```

```
teste2 
```

```
teste2 
```

```
teste2 
```

```
teste2 
```

```
teste2 
```
