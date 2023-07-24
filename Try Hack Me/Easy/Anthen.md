# Anthem
> ### Task1
* ### Scan de portas - Verificando quais portas estão abertas.

```Bash
rustscan -a 10.10.137.229
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f464385-6d3d-44d9-82be-064671ee1e8b)

![image](https://github.com/lufffe/Writeups/assets/90646635/48df6897-9cdb-4572-9f78-c69ff1e2b864)

* ### Verificando o que está rodando nas portas encontradas.
```Bash
nmap -A -p 80,3389 10.10.137.229
```

![image](https://github.com/lufffe/Writeups/assets/90646635/7f568b03-0cd5-469f-a173-ff5c496718a2)

* ### Scan de arquivos e diretorios.
```
gobuster dir -u http://10.10.137.229 -w common.txt -t 100 --no-error
```

![image](https://github.com/lufffe/Writeups/assets/90646635/eea6d5b9-dc3b-4dea-8608-b34092c31d40)

* ### Olhando o contéudo do robots.txt.
![image](https://github.com/lufffe/Writeups/assets/90646635/7d4897d5-ed4f-4654-9bfa-962152fa5599)

* ### Dominio encontrado.
![image](https://github.com/lufffe/Writeups/assets/90646635/352c466f-35fd-40be-91ae-209ce42d6433)

* ### Scan de arquivos e diretorios dentro da pasta umbraco.
```
gobuster dir -u http://10.10.137.229/umbraco/ -w common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/59485aa3-890d-4728-816d-d0be8bf269e0)

* ### Se Pesquisar sobre esse poema encontrará quem é o administrador.
http://anthem.thm/archive/a-cheers-to-our-it-department/
![image](https://github.com/lufffe/Writeups/assets/90646635/2809d49f-8091-4e3e-945a-b722bd27ded8)

* ### Se seguir a mesma ideia do Jane Doe com o emai jd@anthem.com, saberá o email do administrador, para fazer login.
> ### Task2
```
http://10.10.137.229/archive/we-are-hiring/ 
TAG 1
THM{*************}
```

```
view-source:http://10.10.137.229/
TAG 2
THM{*************}
```

```
http://10.10.137.229/authors
TAG3
THM{*********}
```

```
view-source:http://10.10.137.229/archive/a-cheers-to-our-it-department/
TAG4
***{************}
```
> ### Task3
```
rdesktop 10.10.137.229    
```
sg / ******************

![image](https://github.com/lufffe/Writeups/assets/90646635/8aa5d204-409e-4a8c-8ce2-ce2a22acf2b9)

* ### Tem uma pasta backup oculta no c:\ precisa apenas colocar as permissões no arquivo que está lá.
![image](https://github.com/lufffe/Writeups/assets/90646635/a9d9355d-5590-45a5-beb7-e2e555d29c2b)

* ### Senha do administrador no arquivo.

![image](https://github.com/lufffe/Writeups/assets/90646635/74725ff7-1a19-4c1a-b315-53ebe32d9731)

