# ****Bank****


```bash
rustscan -a 10.10.10.29
```
![image](https://github.com/lufffe/Writeups/assets/90646635/419b7fc3-f7d0-48dc-917a-ffab676c82a1)

```bash
nmap -A -p 22,53,80 10.10.10.29
```
![image](https://github.com/lufffe/Writeups/assets/90646635/168cee92-598a-457d-9169-836e8a792f17)

http://bank.htb/login.php
![image](https://github.com/lufffe/Writeups/assets/90646635/d2927f89-3558-4bfd-9d7d-3c69be2a4b8b)

```bash
gobuster dir -w directory-list-2.3-medium.txt -u http://bank.htb/ -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6796d153-aa84-44d5-a798-5b5b30c9cfee)

![image](https://github.com/lufffe/Writeups/assets/90646635/32096070-fcba-4036-82a4-53c92442352a)

![image](https://github.com/lufffe/Writeups/assets/90646635/4209d36f-6331-4b93-8031-570033c5913f)

Email: chris@bank.htb
Password: !##HTBB4nkP4ssw0rd!##

![image](https://github.com/lufffe/Writeups/assets/90646635/4e424d9b-c9b2-40be-a133-20f770f1a1ce)

REVERSE SHELL COM EXTENÇÃO EM .HTB
![image](https://github.com/lufffe/Writeups/assets/90646635/7c8ad05c-40e4-4cea-b31c-388748699308)

www-data@bank:/home/chris$ 

```bash
cat user.txt
```

```bash
find / -perm -u=s -type f 2>/dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/814cbb1a-b0ef-4bf1-b6e8-db43cd1a75d3)

![image](https://github.com/lufffe/Writeups/assets/90646635/689d2822-6570-4a5a-8c2d-10c97170ae6f)

```bash
 cat /root/root.txt
```
