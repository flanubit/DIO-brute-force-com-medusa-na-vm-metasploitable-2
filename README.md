# Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux

Um projeto do bootcamp Riachuelo Cibersegurança na plataforma de ensino DIO.
1. Força bruta em FTP
2. Automação de tentativas em formulário Web
3. Password Spraying em SMB

## Força bruta em FTP

Use **msfadmin** como usuário e senha na vm Metasploitable 2:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Captura%20de%20tela%202026-03-05%20215519.png)

Confira o o IP da máquina Metasploitable 2 usando o comando **ip addr**, neste caso o ip é **192.168.56.102**:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Captura%20de%20tela%202026-03-05%20215619.png)

Abra a outra vm com o Kali Linux instalado, e seguida use o comando **ping -c 3 198.168.56.102** para enviar 3 pacotes ping e testar conexão com a vm Metasploitable 2:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_19-57-08.png)

Após o **ping** use o comando **nmap -sV -p 21,22,80,445,139 192.168.56.102** para procurar pelas portas informadas com o parâmetro **-p**, verificar se estão abertas e qual versão do serviço estão executando nelas com o parâmetro **-sV**:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_20-01-11.png)

Agora tente se conectar ao serviço **FTP** na vm Metasploitable 2 usando o comando **ftp 192.168.56.102**, você verá uma tela semelhante a essa abaixo se houver conexão, porém ainda não sabemos o usuário e senha para acessar:

![](https://github.com/flanubit/brute-force-com-medusa-na-vm-metasploitable-2-DIO/blob/main/images/Screenshot_2026-03-05_20-04-09.png)

## Automação de tentativas em formulário Web

...

## Password Spraying em SMB

...
