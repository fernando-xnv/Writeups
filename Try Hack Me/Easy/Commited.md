  # Commited

* ### Scan de portas.
```bash
rustscan -a 10.10.86.130
```
![image](https://github.com/lufffe/Writeups/assets/90646635/b1d85e8a-a067-49aa-8b4b-ef80ff363a70)

![image](https://github.com/lufffe/Writeups/assets/90646635/e1cde616-54a3-4dde-893d-1b7acfdedd22)

* ### Verificando o que está rodando nas portas encontradas.
```bash
nmap -A -p 22,80,8000 10.10.86.130
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1dc56a6f-766f-4f18-8de8-1403d83bd811)

* ### Verificando o Http.
![image](https://github.com/lufffe/Writeups/assets/90646635/57523e58-fc35-4de5-878f-7903951f3146)

* ### Na Maquina de Ataque tem um arquivo, como a porta 8000 está aberta, e está rodando python3 nela, vamos subir um servidor lá.
![image](https://github.com/lufffe/Writeups/assets/90646635/422c89cb-2306-4319-92e6-b8c29170f939)

* ### Um ip addr para descobrir o ip da maquina e é o mesmo ip que iniciamos.
![image](https://github.com/lufffe/Writeups/assets/90646635/d1a08ab4-757f-46bc-80fa-b01c063caee4)

* ### Subindo servidor em python3.
```bash
python3 -m http.server
```
![image](https://github.com/lufffe/Writeups/assets/90646635/21186614-619d-4780-a4d3-4f29ecd577e9)

* ### Puxando o arquivo encontrado na maquina.
```bash
wget http://10.10.86.130:8000/commited.zip
```
![image](https://github.com/lufffe/Writeups/assets/90646635/1d2f3837-8982-4025-a0f9-3e604aca6103)

* ### Extraindo arquivos.
```bash
unzip commited.zip
```
![image](https://github.com/lufffe/Writeups/assets/90646635/61a530ab-8d6d-4247-925b-57edc17d9a62)

* ### Procurando Commits antigos.
```bash
git log -all
```
![image](https://github.com/lufffe/Writeups/assets/90646635/c462dc24-4912-4f13-8fd7-a1ca26d11db6)

* ### Encontrando a flag em um dos commits.
```bash
git show 
```
![image](https://github.com/lufffe/Writeups/assets/90646635/8f210b57-368c-4a9d-9f13-470a3f68e822)


