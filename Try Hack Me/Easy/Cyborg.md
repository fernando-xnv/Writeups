<h1><b>Segue Writeup da maquina Cyborg do Try Hack Me</h1>

Enumeração das portas com NMAP

```
┌──(xnv㉿kali)-[~]
└─$ nmap -A 10.10.162.202
Starting Nmap 7.91 ( https://nmap.org ) at 2021-09-18 01:03 EDT
Nmap scan report for 10.10.162.202 (10.10.162.202)
Host is up (0.23s latency).
Not shown: 998 closed ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.10 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 db:b2:70:f3:07:ac:32:00:3f:81:b8:d0:3a:89:f3:65 (RSA)
|   256 68:e6:85:2f:69:65:5b:e7:c6:31:2c:8e:41:67:d7:ba (ECDSA)
|_  256 56:2c:79:92:ca:23:c3:91:49:35:fa:dd:69:7c:ca:ab (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 59.38 seconds
```

Enumeração de arquivos e pastas com o WFUZZ.

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.162.202/FUZZ -t 100

000000001:   200        375 L    968 W      11321 Ch    "http://10.10.162.202/"
000000286:   301        9 L      28 W       314 Ch      "admin"
000001505:   301        9 L      28 W       312 Ch      "etc"
000002020:   200        375 L    968 W      11321 Ch    "index.html"  
```

Depois de verificar os resultados encontrei esse arquivo.
```
http://10.10.162.202/etc/squid/passwd
music_archive:$apr1$BpZ.Q.1m$F0qqPwHSOG50URuOVQTTn.
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

```
teste
```

