# BOLT

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.161.172
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5b5d200f-4f0f-400f-9ef1-56a86aef7ea8)

![image](https://github.com/lufffe/Writeups/assets/90646635/f929ae32-7464-49b4-b39d-2a2f8653a02b)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80,8000 10.10.161.172
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1a22ac27-df9f-4d6f-ac02-66c45dba9c60)

![image](https://github.com/lufffe/Writeups/assets/90646635/78dc05c0-662f-46ae-9b44-6384688f4a1e)

```bash
gobuster dir -u http://10.10.161.172:8000 -w ~/directory-list-2.3-small.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0fe18f32-fc50-46e1-8c0e-e62f733ba2b2)

* ### Na página principal você consegue encontrar o usuário e password do CMS.
![image](https://github.com/lufffe/Writeups/assets/90646635/92508fa6-8cb9-4f20-bcc5-1c9ce474d744)


![image](https://github.com/lufffe/Writeups/assets/90646635/b108b8fa-6b31-4172-aac7-bfecd920d738)

* ### Preencha com as informações que estão marcadas com branco.
![image](https://github.com/lufffe/Writeups/assets/90646635/22c8783a-73d1-4a85-9568-1a18183b8c83)

* ### E ganhe acesso de root.
![image](https://github.com/lufffe/Writeups/assets/90646635/cd187a4a-bf2c-43ad-8590-31467bcc5364)

* ### E ai está a flag.
```bash
find / | grep "flag.txt"
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8e7323f1-c511-44bc-97f3-85f989b991d2)



