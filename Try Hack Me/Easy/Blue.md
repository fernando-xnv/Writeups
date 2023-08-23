# Blue

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.66.85
```
![image](https://github.com/lufffe/Writeups/assets/90646635/2cbe8642-97e4-4c76-9623-64f90817740b)

![image](https://github.com/lufffe/Writeups/assets/90646635/31ff32b0-4b55-4647-a2c6-1b4d9a0d4008)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 135,139,445,3389,49152,49153,49154,49158,49160 10.10.66.85
```
![image](https://github.com/lufffe/Writeups/assets/90646635/465eda3d-eab8-4764-9791-d3b115c0e0dc)

* ### Dica.
![image](https://github.com/lufffe/Writeups/assets/90646635/43fb735f-f7d7-4bdd-8225-acf5ebc61c02)

![image](https://github.com/lufffe/Writeups/assets/90646635/c0cdeb4e-56c6-43fa-a46f-9a029b9ca01f)


* ### Abrindo o Metasploit e pesquisando sobre o MS17-010.
![image](https://github.com/lufffe/Writeups/assets/90646635/8e0cdef5-84c2-41b3-a821-f8dfd73e4cc5)

* ### Mude o LHOST E RHOSTS.
![image](https://github.com/lufffe/Writeups/assets/90646635/4149dff9-501d-40a3-b397-1c825dcb1533)

* ### E então é só executar e pegar a shell.
![image](https://github.com/lufffe/Writeups/assets/90646635/21767dad-8987-49da-9561-2c17295606ce)

* ### Aqui tem as hash das senhas dos usuários, e vamos tentar pegar o Jon.
  
meterpreter > hashdump

![image](https://github.com/lufffe/Writeups/assets/90646635/a8c1cc63-d055-4280-8ba2-9bda1a110345)

* ### Quebrando a senha do usuário
![image](https://github.com/lufffe/Writeups/assets/90646635/f9e63581-d5b2-419d-9335-ab64f7818efb)

* ### Pesquisando as flags.
![image](https://github.com/lufffe/Writeups/assets/90646635/f72508ff-ff61-4c9a-89f9-e0c88962426e)
