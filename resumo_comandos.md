## Comando linux:


### Mostra o nivel no sistema de arquivos:

>pwd - mostra o nivel na arvore de diretórios

```
jeancviana@DESKTOP-6SOQARG:~$ pwd
/home/jeancviana
``` 

### Verificar informações do usuario:

> who - info dos users autenticados

```
root@interno:/tmp# who
analista tty7         2023-01-09 20:43 (:0)
```

>whoami - mostra o user logado

```
jeancviana@DESKTOP-6SOQARG:~$ whoami
jeancviana
```

> id - verificar os grupos que o usuario faz parte

```
root@interno:~# id
uid=0(root) gid=0(root) grupos=0(root)
root@interno:~# 
```

> w : exibe informações sobre os usuários atualmente na máquina e seus processos . O cabeçalho da saída mostra (nesta ordem): a hora atual, há quanto tempo o sistema está em execução, quantos usuários estão conectados no momento e a média de carga do sistema nos últimos 1, 5 e 15 minutos  

```
root@interno:/tmp# w
 20:07:59 up  3:23,  1 user,  load average: 0,05, 0,04, 0,00
USUARIO  TTY     DE               LOGIN@   OCIOSO JCPU   PCPU O QUE
analista tty7     :0               seg20   47:25m 43.82s  0.27s xfce4-session
```

> :0 - indica que o user logou no ambiente grafico  
> tty7 - numero da sessão do terminal  

### Tipos de usuarios:

> usuario comum: poucos privilégios  
> usuario root: usuario adm do sistema  

### Comando su:

> su - : para subir a sessão como root com as variaveis de sistema do usuario  

```
jeancviana@DESKTOP-6SOQARG:~$ su - root  
Palavra-passe:  
root@DESKTOP-6SOQARG:~#  
```

### Nome da máquina:

> hostname : traz o nome da máquina  

```
root@DESKTOP-6SOQARG:/etc# hostname  
DESKTOP-6SOQARG  
root@DESKTOP-6SOQARG:/etc#  
```

### Vendo informações da máquina:

> hostnamectl : traz maiores informações sobre a máquina  

```
analista@debian:~$ hostnamectl
   	Static hostname: debian
         Icon name: computer-vm
           Chassis: vm
        Machine ID: ff5ce99eac784cddb2ebb3a00b1d1eb9
           Boot ID: 87bb4c2fb0724e2da268c03a0241afdb
    	Virtualization: oracle
  	Operating System: Debian GNU/Linux 11 (bullseye)
            Kernel: Linux 5.10.0-20-amd64
      Architecture: x86-64
```

### Setando o nome da máquina:

> hostnamectl set-hostname interno.asf.com (TROCANDO O HOSTNAME DA MÁQUINA)

```
analista@debian:~$ hostnamectl set-hostname interno.asf.com
analista@debian:~$ hostnamectl 
   Static hostname: interno.asf.com
         Icon name: computer-vm
           Chassis: vm
        Machine ID: ff5ce99eac784cddb2ebb3a00b1d1eb9
           Boot ID: 87bb4c2fb0724e2da268c03a0241afdb
    Virtualization: oracle
  Operating System: Debian GNU/Linux 11 (bullseye)
            Kernel: Linux 5.10.0-20-amd64
      Architecture: x86-64
analista@debian:~$ 
```

### Comando para caminhar na arvore de diretórios:

> cd + caminho do arquivo por exemplo cd /home/analista ou cd ~/analista  
> cd /: vai para o diretório raiz  
> cd ~: vai para o diretório home  
> cd .. ou cd ../../ : volta a quantidade de niveis digitados  
> cd - : volta para o diretório anterior  
>   
> . caminho do diretório atual  
> .. caminho do diretório anterior  

## Sistema de diretórios FHS Filesystem Hierarchy Standard:

> O Filesystem Hierarchy Standard (“FHS”) é um padrão na hierarquia do sistema GNU/Linux.  
>  
> /       :diretório raiz  
>   
> /bin    : Este diretório contém os comandos básicos para todos os usuários (cp, mv, rm…). Esses são os comandos necessários para iniciar o sistema.  
>   
> /boot   :Aqui é onde os arquivos do seu carregador de boot (GRUB, por exemplo) e os kernels do Linux estão localizados.  
>   
> /dev    :Links para periféricos físicos (CDs, discos rígidos, etc.), bem como periféricos virtuais (/dev/null, /dev/random). Observe que os dispositivos físicos são nomeados como /dev/sdXN com X sendo uma letra e N um número: /dev/sda1 representa a primeira partição (1) de seu primeiro disco rígido (a) ou /dev/sdd6 representa a sexta partição (6) de seu quarto disco rígido (d) …  
>   
> /etc    :Este é o local dos arquivos globais de configuração dos programas instalado.  
>   
> /home   :Diretório que contém as pastas do usuário no formato /home/nome-do-usuário.  
>   
> /lib:   Diretório onde as bibliotecas do sistema estão instaladas.  
>   
> /mnt    :Ponto de montagem para partições internas montadas temporariamente. As partições de discos rígidos internos geralmente são montadas aqui. Para partições externas, usaremos /media em seu lugar.  
>  
> /media  :Equivalente a /mnt, mas para mídia removível/externa.  
>  
> /opt    :É reservado para instalar pacotes de aplicativos extras, baixados da Internet, como o Google Chrome.  
>   
> /proc   :Sistema de arquivos virtual apresenta informações sobre processos e outras informações de sistema em uma estrutura hierárquica semelhante a arquivos, fornecendo um método mais conveniente e padronizado para acessar dinamicamente dados de processos armazenados no núcleo do que os métodos de rastreamento tradicionais ou acesso direto à memória do núcleo. (Wikipedia, 2020)  
>   
> /root   :Diretório do usuário root.  
>   
> /sbin   :Série de executáveis ​​para administradores.  
>   
> /srv    :Dados para serviços hospedados pelo sistema. Por exemplo, conteúdo de um servidor web (HTTP) ou de um banco de dados.  
>   
> /tmp    :Diretório de arquivos temporários, esvaziado cada vez que o sistema é iniciado.  
>   
> /usr    :Pasta contendo os executáveis ​​do sistema que não são vitais para sua inicialização e seu funcionamento mínimo.  
>   
> /var    :Pasta com conteúdos de dados variáveis ​​do sistema, indicando seu status. Dividido em subpastas.  

### Criando arquivos vazios:

> touch : cria arquivo em branco  
> touch arquivo1: cria o arquivo em branco arquivo1 podem sem criados varios arquivos em sequencia touch arquivo1 touch arquivo2   
> touch doc0{1..5}.txt para criar arquivos em sequência.  

### Apagando diretório e arquivos:

> rm - apaga arquivos  
> rm -rf : -r forma recursiva para apagar arquivos, -f força apagar sem pedir permissão (sem chance de salvação)  
> rm -rfd : -d apaga o diretório (sem chance de salvação)  
> rmdir: apaga diretório mas tem que estar vazio  

### Comando History:

> history: comando para visualizar histórico de comandos executados no terminal

```
root@interno:~# history
    1  cd /mnt/
    2  ls
    3  cd ..
```
> voce pode informar o numero de linhas que quer ver no history como ocomando history + quantidade de linhas

```
root@interno:~# history 10
   68  who -a
   69  clear
   70  id
   71  clear
   72  histroy
   73  history
   74  history 71
   75  history --help
   76  man history
   77  history 10
root@interno:~# 
```
> voce pode usar o comando grep para filtrar o comando history | grep w*

```
root@interno:~# history | grep apt*  
   21  apt search kernel  
   22  apt search kernel |grep header  
   23  apt install linux-headers  
   24  apt install linux-headers-`uname -r`  
   30  apt install ./google-chrome-stable_current_amd64.deb   
   31  apt --fix-broken install  
   32  apt install ./google-chrome-stable_current_amd64.deb   
   37  apt update  
root@interno:~#   
```

> após localizar o arquivo voce pode dar o comando ! + o numero do comando no history para refazer o comando

```
root@interno:~# !62
apt-get autoremove
Lendo listas de pacotes... Pronto
Construindo árvore de dependências... Pronto
Lendo informação de estado... Pronto        
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.
root@interno:~# 
```

> verificar quantidades de linhas máximo no history

```
root@interno:~# echo $HISTSIZE
500
```

> echo $HISTFILE mostra o caminho do arquivo do history  

```
root@interno:/# echo $HISTFILE
/root/.bash_history
```

> limpar o history -c

```
root@interno:~# history -c
root@interno:~# history
    1  history
root@interno:~# 
```

> history -w salva as mudanças efetuadas no history

```
root@interno:/# history -w 
root@interno:/# 
root@interno:/# 
root@interno:/# history
    1  history
    2  history -w 
    3  history
root@interno:/#
```

> fc -l também é usado para ver o history  

```
root@interno:/# history -w 
root@interno:/# 
root@interno:/# 
root@interno:/# history
    1  history
    2  history -w 
    3  history
root@interno:/#
```

> CTRL+R faz buscas no historico igual ao comando history  

```
(failed reverse-i-search)`texto':  
```

> Seta cima ou baixo para navegar pelos comandos  

### Comando para limpar tela do terminal

> clear

```
root@interno:~# clear^C
root@interno:~# 
```

### Comando mv

> mv: movimenta e renomeia arquivos:  
>  
> Renomeia:  

```
root@interno:/tmp# mv doc02.txt arquivo02.txt 
root@interno:/tmp# ls -lh
total 24K
-rw-r--r-- 1 root     root        0 jan 10 20:33 '[1,2]'
-rw-r--r-- 1 root     root        0 jan 11 19:37  arquivo02.txt
```

> Movimenta  

```
root@interno:/tmp# cd /
root@interno:/# mv /tmp/arquivo02.txt /opt/
root@interno:/# ls /opt/
arquivo02.txt  google  VBoxGuestAdditions-7.0.4
root@interno:/# mv /opt/arquivo02.txt /tmp/
```

### Comando cp

> cp: copia arquivos e pastas, opção -r de recursive para copiar pasta -p mantém as permissões do arquivo. cp + caminho do arquivo ou pasta a ser copiado + arquivo ou pasta destino

```
root@interno:/tmp# cp -rp /etc/passwd . (. significa a pasta em que vc se encontra atualmente)
root@interno:/tmp# ls -lh
total 28K
-rw-r--r-- 1 root     root        0 jan 10 20:33 '[1,2]'
-rw-r--r-- 1 root     root        0 jan 11 19:37  arquivo02.txt
srwxrwxrwx 1 analista analista    0 jan  9 20:43  dbus-EevGmrHoJr
drwxr-xr-x 9 root     root     4,0K jan 10 19:20  log
-rw-r--r-- 1 root     root     2,1K dez 19 19:41  passwd
```

> Também é possivel copiar o arquivo mudando o seu nome:  

```
root@interno:/tmp# 
root@interno:/tmp# cp arquivo02.txt arquivo01.txt
root@interno:/tmp# ls
arquivo01.txt
arquivo02.txt
```

### Arquivos de Ajuda

> man : manual do linux, comando man +nome do comando a ser pesquisado

```
root@interno:/# man cp
root@interno:/#

> help : traz lista de comandos

```
root@interno:/# help
GNU bash, versão 5.1.4(1)-release (x86_64-pc-linux-gnu)
Esses comandos shell são definidos internamente. Digite `help' para ver essa
lista. Digite `help NOME' para descobrir mais sobre a função `NOME'.
```

> help cd : traz uma ajuda resumida do comando solicitado  

```
root@interno:/# help cd
cd: cd [-L|[-P [-e]] [-@]] [DIR]
    Altera o diretório de trabalho do shell.
    
    Altera o diretório atual para DIR, sendo o padrão de DIR o mesmo valor
    da variável HOME.      
```

> info : outro arquivo de ajuda sobre o linux, comando info + comando a ser pesquisado

```
root@interno:/# info ls
root@interno:/# 
```








