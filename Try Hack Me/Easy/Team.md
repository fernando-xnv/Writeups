# Team

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.4.169
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f01a0be-ebec-49ca-9224-1370ce6dc092)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 21,22,80 10.10.4.169
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9c6a0cee-6596-415b-9509-899b399ad85f)

* ###  Scan de Arquivos e Diretórios.
```bash
* gobuster dir -u http://team.thm -w ~/common.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/60f5f9bd-bd6a-49d2-9e14-999e01b389e8)

* ###  Olhando robots.txt
![image](https://github.com/lufffe/Writeups/assets/90646635/541242b1-9762-4ceb-80a4-13f9e0698252)
