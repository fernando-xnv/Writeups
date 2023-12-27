# ****10.10.10.3 - Lame****

```bash
rustscan -a 10.10.10.4
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d5a20a01-fc19-4129-b59f-8d1568842e27)


```bash
nmap -A -p 135,139,445 10.10.10.4
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ecfa94ea-8cee-4817-9c38-08353cc9988c)

```bash
nmap -v -script smb-vuln* -p 139,445 10.10.10.4
```
![image](https://github.com/lufffe/Writeups/assets/90646635/eaecec0a-da46-4baa-9290-71ec247b74b3)

```bash
msfconsole
```
![image](https://github.com/lufffe/Writeups/assets/90646635/75399ce6-7f11-4306-a474-0ee600582817)

```bash
search ms08-067
```
