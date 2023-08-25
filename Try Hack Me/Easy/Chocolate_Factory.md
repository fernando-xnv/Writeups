
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




